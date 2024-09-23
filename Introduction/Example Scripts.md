# Example Scripts

Find other example scripts on our [GitHub Repositories](https://github.com/hake-me?tab=repositories)

---

* ### Auto Join Guild

  ```
  local joiner = {}

  local last_guild_want_join = nil
  local last_guild_result = ""
  local next_time = os.clock()

  -- change this if you want it to take longer to try joining
  local cooldown_time = 60.0 * 5.0

  function joiner.OnGCMessageReceived(msg)
      if msg.name == "k_EMsgClientToGCJoinGuildResponse" then
          local data = msg.GetArguments()

          if data.result.name == "k_eSuccess" and last_guild_want_join ~= nil then
              last_guild_want_join = nil
              Engine.ExecuteCommand("snd_sos_start_soundevent ui.guild_joined")
          end

          last_guild_result = data.result.name

          return
      end 
  end

  function joiner.OnGCMessageSend(msg)
      if msg.name == "k_EMsgClientToGCJoinGuild" then
          local data = msg.GetArguments()
          if data.guild_id == nil then return end

          last_guild_want_join = data.guild_id
          next_time = os.clock() + cooldown_time

          return
      end
  end

  function joiner.OnDraw()
      if last_guild_want_join == nil then return end
      if os.clock() < next_time then return end

      local msg = Protobuf.Create("k_EMsgClientToGCJoinGuild")
      msg["guild_id"] = last_guild_want_join
      GCClient.SendMessage(msg)

      next_time = os.clock() + cooldown_time
  end

  function joiner.OnUI()
      if UI.BeginWindow("Guild Joiner") then
          UI.Label("Last result: " .. last_guild_result)

          if last_guild_want_join == nil then
              UI.Label("Guild Joiner waiting for guild to join.")
              UI.Label("Try joining a guild.")
              UI.EndWindow()
              return
          end

          local now = os.clock()
          local diff = math.floor(next_time - now)

          UI.Label("Attempting to join " .. tostring(last_guild_want_join))
          UI.SliderInt("Rejoining in", diff, 0, cooldown_time)

          local changed, value = UI.SliderFloat("Cooldown Time", cooldown_time, 1, 60 * 5)

          if changed then
              cooldown_time = math.floor(value)
              next_time = now + math.min((next_time - now), cooldown_time)
          end

          UI.EndWindow()
      end
  end

  return joiner
  ```
* ### Auto High-Five

  ```
  local auto_hf = { 
      enabled = Menu.AddOption({ "AutoHighFive" }, "Auto High Five", "", 0, 1, 1, 1),
      spam = Menu.AddOption({ "AutoHighFive" }, "Spam High Five", "", 0, 1, 1, 0)
  }

  local next_time = 0
  local range = 0

  function auto_hf.OnUpdate()
      local now = os.clock()

      if Menu.GetValue(auto_hf.enabled) == 0 then return end
      if now < next_time then return end

      local me = Heroes.GetLocal()
      if not Entity.IsAlive(me) then return end

      local high_five = NPC.GetAbility(me, "high_five")
      if not high_five or not Ability.IsReady(high_five) or NPC.HasModifier(me, "modifier_high_five_requested") then 
          next_time = now + 0.5
          return 
      end

      if range == 0 then
          range = Ability.GetLevelSpecialValueFor(high_five, "acknowledge_range")
      end

      local should_spam = Menu.GetValue(auto_hf.spam) == 1

      for i=1, Heroes.Count() do
          local hero = Heroes.Get(i)

          if hero ~= me and Entity.IsAlive(hero) and not Entity.IsDormant(hero) 
             and NPC.IsEntityInRange(me, hero, range) 
             and (should_spam or NPC.HasModifier(hero, "modifier_high_five_requested")) then
              Ability.CastNoTarget(high_five)
              next_time = now + 0.5
              break;
          end
      end
  end

  return auto_hf
  ```
* ### Ember Spirit Sleight of Fist Visualization/Auto Use

  Example script to figure out where to cast Sleight of Fist with the least turn/travel time. Can be auto casted by holding F.

  ```
  local e = {}

  local last_radius = 0
  local particle = nil

  function e.OnDraw()
      local me = Heroes.GetLocal()
      if me == nil then return end

      local sleight_of_fist = NPC.GetAbility(me, "ember_spirit_sleight_of_fist")
      if sleight_of_fist == nil then return end

      local cast_range = Ability.GetCastRange(sleight_of_fist)
      local radius = Ability.GetLevelSpecialValueFor(sleight_of_fist, "radius")

      -- Create a particle
      if particle == nil or radius ~= last_radius then
          if particle then 
              Particle.Destroy(particle)
          end

          particle = Particle.Create("particles/ui_mouseactions/range_display.vpcf", Enum.ParticleAttachment.PATTACH_CUSTOMORIGIN, me)
          last_radius = radius
      end

      local my_pos = Entity.GetAbsOrigin(me)
      local rot = Entity.GetAbsRotation(me)
      local forward = rot:GetForward()
      local end_pos = my_pos + forward:Scaled(cast_range)

      local sx, sy, svis = Renderer.WorldToScreen(my_pos)
      local ex, ey, evis = Renderer.WorldToScreen(end_pos)

      -- Draw our view direction
      if svis and evis then
          Renderer.SetDrawColor(255, 0, 0, 255)
          Renderer.DrawLine(sx, sy, ex, ey)
      end

      local npcs = Entity.GetUnitsInRadius(me, cast_range + radius, Enum.TeamType.TEAM_ENEMY)
      local least = 999
      local nearest_npc = nil

      for _, ent in pairs(npcs) do
          if not Entity.IsDormant(ent) and Entity.IsAlive(ent) then
              local face_time = NPC.GetTimeToFace(me, ent)
              if  face_time < least then
                  least = face_time
                  nearest_npc = ent
              end
          end
      end

      if nearest_npc ~= nil then
          local ent = nearest_npc
          local ent_pos = Entity.GetAbsOrigin(ent)

          local dir_to_ent = ent_pos - my_pos

          -- Get the nearest position.
          local projected_pos = my_pos + dir_to_ent:Project(forward)

          local delta_to_projection = projected_pos - ent_pos
          local dir_to_projection = delta_to_projection:Normalized()

          -- Correct the nearest position if it's outside the radius of Sleight of Fist.
          if delta_to_projection:Length2D() > radius then
              projected_pos = ent_pos + dir_to_projection:Scaled(radius - NPC.GetHullRadius(ent))
          end

          local delta_to_projection_from_me = projected_pos - my_pos
          local dir_to_projection_from_me = delta_to_projection_from_me:Normalized()

          -- Fix cast range
          if delta_to_projection_from_me:Length2D() > cast_range then
              projected_pos = my_pos + dir_to_projection_from_me:Scaled(cast_range)
          end

          -- Fix values
          delta_to_projection = projected_pos - ent_pos
          dir_to_projection = delta_to_projection:Normalized()

          -- Update particle positions
          Particle.SetControlPoint(particle, 0, projected_pos)
          Particle.SetControlPoint(particle, 1, Vector(radius, 0, 0))

          local x, y, vis = Renderer.WorldToScreen(projected_pos)

          if vis then
              Renderer.SetDrawColor(0, 255, 0, 255)
              Renderer.DrawFilledRect(x - 5, y - 5, 10, 10)
          end

          -- Test the result
          if Input.IsKeyDown(Enum.ButtonCode.KEY_F) then
              Ability.CastPosition(sleight_of_fist, projected_pos)
          end
      else
          Particle.Destroy(particle)
          particle = nil
      end
  end

  return e
  ```
* ### Matchmaking debug

  ```
  local mm = {}

  local GAME_MODES = {
      DOTA_GAMEMODE_NONE = 1 << 0,
      DOTA_GAMEMODE_AP = 1 << 1,
      DOTA_GAMEMODE_CM = 1 << 2,
      DOTA_GAMEMODE_RD = 1 << 3,
      DOTA_GAMEMODE_SD = 1 << 4,
      DOTA_GAMEMODE_AR = 1 << 5,
      DOTA_GAMEMODE_INTRO = 1 << 6,
      DOTA_GAMEMODE_HW = 1 << 7,
      DOTA_GAMEMODE_REVERSE_CM = 1 << 8,
      DOTA_GAMEMODE_XMAS = 1 << 9,
      DOTA_GAMEMODE_TUTORIAL = 1 << 10,
      DOTA_GAMEMODE_MO = 1 << 11,
      DOTA_GAMEMODE_LP = 1 << 12,
      DOTA_GAMEMODE_POOL1 = 1 << 13,
      DOTA_GAMEMODE_FH = 1 << 14,
      DOTA_GAMEMODE_CUSTOM = 1 << 15,
      DOTA_GAMEMODE_CD = 1 << 16,
      DOTA_GAMEMODE_BD = 1 << 17,
      DOTA_GAMEMODE_ABILITY_DRAFT = 1 << 18,
      DOTA_GAMEMODE_EVENT = 1 << 19,
      DOTA_GAMEMODE_ARDM = 1 << 20,
      DOTA_GAMEMODE_1V1MID = 1 << 21,
      DOTA_GAMEMODE_ALL_DRAFT = 1 << 22,
      DOTA_GAMEMODE_TURBO = 1 << 23,
      DOTA_GAMEMODE_MUTATION = 1 << 24,
      DOTA_GAMEMODE_COACHES_CHALLENGE = 1 << 25,
  }

  local mode_names = {}

  for k, v in pairs(GAME_MODES) do
      table.insert(mode_names, k)
  end

  table.sort(mode_names)

  local selected_mode = 1

  function mm.OnUI()
      if UI.BeginWindow("MM Debug") then
          if UI.TreePush("Real Modes") then
              local dota_match_game_modes = CVar.FindVar("dota_match_game_modes")
              local dota_competitive_game_modes = CVar.FindVar("dota_competitive_game_modes")

              for _, mode_name in ipairs(mode_names) do
                  local mode_value = GAME_MODES[mode_name]
                  local current_cvar = CVar.GetVarInt(dota_match_game_modes)
                  local has_mode = (current_cvar & mode_value) ~= 0

                  local changed, value = UI.Checkbox(mode_name, has_mode)

                  if changed then
                      CVar.SetVarValues(dota_match_game_modes, current_cvar ~ mode_value)
                      CVar.SetVarValues(dota_competitive_game_modes, current_cvar ~ mode_value)
                  end
              end
          end

          if UI.Button("Find") then
              local dota_match_game_modes = CVar.FindVar("dota_match_game_modes")
              local dota_competitive_game_modes = CVar.FindVar("dota_competitive_game_modes")
              CVar.SetVarValues(dota_match_game_modes, GAME_MODES.DOTA_GAMEMODE_ALL_DRAFT)
              CVar.SetVarValues(dota_competitive_game_modes, GAME_MODES.DOTA_GAMEMODE_ALL_DRAFT)
              Matchmaking.FindMatch(Enum.MatchType.MATCH_TYPE_COMPETITIVE)
          end
          UI.ToggleButton("IsFindingMatch", Matchmaking.IsFindingMatch())
          UI.ToggleButton("IsInGame", Matchmaking.IsInGame())
          UI.ToggleButton("IsInLobby", Matchmaking.IsInLobby())

          if UI.Button("Cancel") then
              Matchmaking.StopFindingMatch()
          end

          UI.EndWindow()
      end
  end

  return mm
  ```
* ### Simple Filesystem
* ### Draw IO spirits status

  ```
  local Aimbot = {}

  local spirits = {}
  local first_time = true

  -- Test entity and insert if spirit.
  local function insert_potential_spirit(ent)
      if Entity.GetClassName(ent) == "C_DOTA_Wisp_Spirit" then
          Log.Write("Spirit found")
          spirits[ent] = true
      end
  end

  -- Cache all spirit entities.
  local function update_spirit_entities()
      for i=1, NPCs.Count() do
          local npc = NPCs.Get(i)

          insert_potential_spirit(npc)
      end
  end

  -- Checks if spirit is active
  local function is_valid_spirit(spirit)
      if Entity.GetLastMessageTime(spirit) + GlobalVars.GetTickInterval() < GlobalVars.GetCurTime() or
         Entity.GetViewerID(spirit) == -1 or 
         (Entity.GetEffects(spirit) & Enum.EntityEffect.EF_NODRAW) ~= 0 or 
         Entity.IsDormant(spirit) then
          return false
      end

      return true
  end

  local spirits_speed = 0.0
  local last_spirits_distance = 0.0
  local font = Renderer.LoadFont("Tahoma", 24)

  local spirits_state = "NO VALID SPIRITS"

  function Aimbot.OnGameStart()
      spirits = {}
      first_time = true
  end

  function Aimbot.OnUpdate()
      -- update spirit entities
      if first_time then
          update_spirit_entities()
          first_time = false
      end

      local me = Heroes.GetLocal()
      local wisp_spirits_in = NPC.GetAbility(me, "wisp_spirits_in")

      -- check if spirits ability is valid
      if wisp_spirits_in == nil or Ability.IsHidden(wisp_spirits_in) then
          spirits_state = "NO VALID SPIRITS"
          return
      end

      local valid_spirit = nil

      -- get first valid spirit to test
      for spirit, _ in pairs(spirits) do
          if is_valid_spirit(spirit) then
              valid_spirit = spirit
              break
          end
      end

      if valid_spirit == nil then
          spirits_state = "NO VALID SPIRITS"
          return 
      end

      local my_pos = Entity.GetAbsOrigin(me)
      local spirit_pos = Entity.GetOrigin(valid_spirit)

      local spirit_distance = (spirit_pos - my_pos):Length2D()

      -- How fast are the spirits going in/out
      spirits_speed = spirit_distance - last_spirits_distance
      last_spirits_distance = spirit_distance

      -- Draw whether the spirits are going inwards or outwards
      if spirits_speed > 0.1 then
          spirits_state = "Out"
      elseif spirits_speed < -0.1 then
          spirits_state = "In"
      else
          spirits_state = "Stationary"
      end
  end

  function Aimbot.OnDraw()
      local me = Heroes.GetLocal()
      if me == nil then return end

      local x, y, visible = Renderer.WorldToScreen(Entity.GetAbsOrigin(me))

      if visible then
          -- Draw whether the spirits are going inwards or outwards
          Renderer.SetDrawColor(255, 0, 0, 255)
          Renderer.DrawTextCenteredX(font, x, y - 10, spirits_state)
      end
  end

  -- Catch any new spirits here.
  function Aimbot.OnEntityCreate(ent)
      insert_potential_spirit(ent)
  end

  function Aimbot.OnEntityDestroy(ent)
      spirits[ent] = nil
  end

  return Aimbot
  ```
* ### Draw all active projectiles

  ```
  local p = {}

  local active_tracking = {}
  local active_linear = {}

  function p.OnProjectile(projectile)
      active_tracking[projectile.handle] = true
  end

  function p.OnLinearProjectileCreate(projectile)
      active_linear[projectile.handle] = true
  end

  function p.OnDraw()
      -- Tracking projectiles
      for handle, _ in pairs(active_tracking) do
          local projectile = Projectiles.GetTrackingProjectileByHandle(handle)

          if projectile ~= nil then
              local x, y, v = Renderer.WorldToScreen(projectile.position)

              Renderer.SetDrawColor(255, 0, 0, 255)
              Renderer.DrawFilledRect(x, y, 10, 10)
          else
              active_tracking[handle] = nil
          end
      end

      -- Linear projectiles
      for handle, _ in pairs(active_linear) do
          local projectile = Projectiles.GetLinearProjectileByHandle(handle)

          if projectile ~= nil then
              local start_x, start_y, start_v = Renderer.WorldToScreen(projectile.start)
              local x, y, v = Renderer.WorldToScreen(projectile.position)

              local end_x, end_y, end_v = Renderer.WorldToScreen(projectile.start + projectile.velocity:Normalized():Scaled(projectile.range))

              if v then
                  Renderer.SetDrawColor(255, 0, 0, 255)
                  Renderer.DrawFilledRect(x, y, 10, 10)
              end

              if end_v then
                  Renderer.SetDrawColor(255, 0, 0, 255)
                  Renderer.DrawFilledRect(end_x, end_y, 10, 10)
              end

              if v and start_v and end_v then
                  -- start to current pos
                  Renderer.SetDrawColor(0, 255, 0, 255)
                  Renderer.DrawLine(start_x, start_y, x, y)

                  -- current pos to end pos
                  Renderer.SetDrawColor(255, 0, 0, 255)
                  Renderer.DrawLine(x, y, end_x, end_y)
              end
          else
              active_linear[handle] = nil
          end
      end
  end

  return p
  ```
* ### Callback Inspector

  ```
  local callback_inspector = {}
  local filtered_names = {}

  local ui_settings = {
      new = function(bool_options)
          return {
              bools = bool_options,

              draw_bools = function(self)
                  for k, v in pairs(self.bools) do
                      local changed, value = UI.Checkbox(v.name, v.val)

                      if changed then
                          v.val = value
                      end
                  end
              end,

              get_bool = function(self, name)
                  return self.bools[name].val
              end
          }
      end,

      bool = function(name, def)
          return { val = def, name = name }
      end
  }

  local function count_table(tbl)
      if tbl == nil then return 0 end

      local count = 0

      for k, v in pairs(tbl) do
          count = count + 1
      end

      return count
  end

  local function new_event(name)
      return 
      {
          count = 1,
          first_time = true,
          last_args = { },
          last_args_count = 0,
          settings = ui_settings.new({
            wants_args = ui_settings.bool("Update Arguments", false),
            cb_disabled = ui_settings.bool("Disable Callback", false)
          }),
          set_args = function(self, args)
              self.last_args = args
              self.last_args_count = count_table(args)
          end
      }
  end

  -- Create a new event table instance
  local function new_event_table()
      return 
      {
          events = {},
          names = {},
          settings = ui_settings.new({ 
              hide_no_args = ui_settings.bool("Hide No Argument Events", false) 
          }),

          insert = function(self, name)
              self.events[name] = new_event(name)
          end,

          -- Callback listeners for this event
          callbacks = 
          {
              ----------------------------------
              -- Create a new callback listener
              -----------------------------------
              new = function(self, object, wants_args)
                  if object.callbacks == nil then return end
                  if wants_args == nil then wants_args = true end

                  for k, cb in pairs(object.callbacks) do
                      -- Create the initial table if it doesn't exist
                      if self[k] == nil then
                          self[k] = {
                              list = {},
                              wants_args = wants_args,

                              -- Invoke the list of functions associated with this callback
                              invoke = function(self, args)
                                  local any_false = false

                                  for i, callback in ipairs(self.list) do
                                      local result = callback:invoke(args)

                                      if not result then 
                                          any_false = true
                                      end
                                  end

                                  return not any_false
                              end
                          }
                      end

                      table.insert(self[k].list, { 
                          object_ = object, 
                          callback_ = cb,

                          invoke = function(self, args)
                              return self.callback_(self.object_, args)
                          end
                      })
                  end
              end,

              new_function_only = function(self, name, func)
                  self:new({ 
                      callbacks = { 
                          [name] = func 
                      }
                  })
              end,

              new_function_w_table = function(self, name, tbl, func)
                  tbl.callbacks = { 
                      [name] = func 
                  }

                  self:new(tbl)
              end
          }
      }
  end

  -- Keeps track of events passed through OnPanoramaUIEvent, etc
  local events = {
      OnProjectile = new_event_table(),
      OnGameEvent = new_event_table(),
      OnCustomGameEvent = new_event_table(),
      OnPanoramaUIEvent = new_event_table(),
      OnNetMessageSend = new_event_table(),
      OnNetMessageReceived = new_event_table(),
      OnGCSharedObjectUpdated = new_event_table(),
      OnGCMessageReceived = new_event_table(),
      OnGCMessageSend = new_event_table(),
      ManuallyCreated = new_event_table(),
      OnParticleCreate = new_event_table(),
      OnStartSound = new_event_table()
  }

  local function label_table(tree_name, t, known, prefix)
      if t == nil then return end
      if prefix == nil then prefix = "" end

      if known == nil then
          known = {}
      end

      if type(t) == "table" then
          if known[t] == nil then
              known[t] = true
          end
      end

      local sorted_t = { }

      for k, arg in pairs(t) do
          table.insert(sorted_t, k)
      end

      -- Sort normally but make tables appear before normal variables
      table.sort(sorted_t, function(a, b)
          if type(t[a]) ~= "table" and type(t[b]) == "table" then
              return false
          elseif type(t[a]) == "table" and type(t[b]) ~= "table" then
              return true
          else
              return tostring(a) < tostring(b)
          end
      end)

      for i, k in ipairs(sorted_t) do
          local arg = t[k]

          if type(arg) == "table" then
              if known[arg] == nil then
                  local tree_pushed = UI.TreePush(prefix .. tostring(k) .. " [" .. tree_name ..  "]: ")

                  if tree_pushed then
                      label_table(tree_name .. "[" .. tostring(k) .. "]", arg, known, prefix .. " ")
                      UI.TreePop()
                  end
              end
          else
              UI.Label(prefix .. tostring(k) .. ": " .. tostring(arg))
          end
      end
  end

  local function draw_tree(name, tbl)
      local tree_pushed = UI.TreePush(name)
      -- So the ID doesn't change
      UI.SameLine()
      UI.Label(": " .. tbl.count)

      if tree_pushed then
          tbl.settings:draw_bools()

          --if #tbl.last_args > 0 then
              label_table(name, tbl.last_args)
          --end

          UI.TreePop()
      end
  end

  -- Example callback that keeps track of a changing data structure
  local callback_example = {
      callbacks = {
          ["CNETMsg_Tick"] = function(self, args)
              local insert_custom = function(name, args)
                  local event_table = events.ManuallyCreated
                  local tbl = event_table.events[name]

                  if tbl ~= nil then
                      tbl.count = tbl.count + 1
                  else
                      table.insert(event_table.names, name)
                      table.sort(event_table.names)

                      event_table:insert(name)
                      tbl = event_table.events[name]
                  end

                  tbl.last_args = args
              end

              -- Not really an event, just a data structure that is changing constantly
              -- We insert it into our event list so we can view it in the window
              -- This does not need to be done here, it could be done anywhere, CNETMsg_Tick callback is just an example
              insert_custom("CSODOTALobby", Matchmaking.GetLobbyData())
              insert_custom("CSODOTAParty", Matchmaking.GetPartyData())
              insert_custom("CSODOTAGameAccountClient", Matchmaking.GetAccountData())
              insert_custom("CMsgStartFindingMatch", Matchmaking.GetMatchSearchData())

              return true
          end,
          ["CMsgSource1LegacyGameEventList"] = function(self, args)
              local descriptors = args.descriptors

              table.sort(descriptors, 
                  function(a, b)
                      return a.name < b.name
                  end)

              for i, descriptor in ipairs(args.descriptors) do
                  Log.Write(descriptor.name .. ": " .. descriptor.eventid)
                  GameEvents.StartListening(descriptor.name)
              end

              return true
          end,
      },
  }

  local panel_loaded = {
      callbacks = {
          PanelLoaded = function(self, args)

              --Log.Write(tostring(args[1].id))
              --Log.Write(" " .. tostring(args[1].paneltype))
              return true
          end
      }
  }

  local game_event = {
      callbacks = {
          entity_hurt = function(self, args)
              local data = args.data

              local attacker = Entities.GetEntityByIndex(data.entindex_attacker)
              local target = Entities.GetEntityByIndex(data.entindex_killed)

              if Entity.IsNPC(attacker) and Entity.IsNPC(target) then
                  Log.Write(NPC.GetUnitName(attacker) .. " -> " .. NPC.GetUnitName(target))
              end

              return true
          end
      }
  }

  local function run_callback(event_table, event)
      local tbl = event_table.events[event.name]

      if tbl ~= nil then
          tbl.count = tbl.count + 1
      else
          table.insert(event_table.names, event.name)
          table.sort(event_table.names)

          event_table:insert(event.name)
          tbl = event_table.events[event.name]
      end

      local get_params = function(event)
          if event.GetArguments ~= nil then
              return event.GetArguments()
          end

          return event
      end

      local callback = event_table.callbacks[event.name]
      local test = ((callback ~= nil and callback.wants_args) or tbl.settings.bools.wants_args.val or tbl.first_time)
      local params = test and get_params(event) or nil
      local invoke_result = true

      if callback then
          if not params then params = {} end
          invoke_result = callback:invoke(params)
      end

      if params then
          if tbl.first_time then tbl.first_time = false end

          tbl:set_args(params)
      end

      -- If true, callback goes through to the game.
      return invoke_result and not tbl.settings.bools.cb_disabled.val
  end

  function callback_inspector.OnScriptLoad()
      events.OnNetMessageReceived.callbacks:new(callback_example)
      events.OnPanoramaUIEvent.callbacks:new(panel_loaded)
      events.OnGameEvent.callbacks:new(game_event)
  end

  function callback_inspector.OnProjectile(projectile)
      local event = {
          name = projectile.name,
          data = projectile
      }

      return run_callback(events.OnProjectile, event)
  end

  function callback_inspector.OnGameEvent(event)
      return run_callback(events.OnGameEvent, event)
  end

  function callback_inspector.OnCustomGameEvent(event)
      return run_callback(events.OnCustomGameEvent, event)
  end

  function callback_inspector.OnNetMessageSend(msg)
      return run_callback(events.OnNetMessageSend, msg)
  end

  function callback_inspector.OnNetMessageReceived(msg)
      return run_callback(events.OnNetMessageReceived, msg)
  end

  function callback_inspector.OnGCSharedObjectUpdated(msg)
      return run_callback(events.OnGCSharedObjectUpdated, msg)
  end

  function callback_inspector.OnGCMessageReceived(msg)
      return run_callback(events.OnGCMessageReceived, msg)
  end

  function callback_inspector.OnGCMessageSend(msg)
      return run_callback(events.OnGCMessageSend, msg)
  end

  function callback_inspector.OnPanoramaUIEvent(event)
      return run_callback(events.OnPanoramaUIEvent, event)
  end

  function callback_inspector.OnParticleCreate(particle)
      local event = {
          name = particle.name,
          data = particle
      }

      return run_callback(events.OnParticleCreate, particle)
  end

  function callback_inspector.OnStartSound(sound)
      local event = {
          name = sound.name,
          data = sound
      }

      return run_callback(events.OnStartSound, sound)
  end

  function callback_inspector.OnUI()
      if UI.BeginWindow("Events") then
          -- global_ui_settings:draw_bools()
          for callback_name, event_table in pairs(events) do
              -- Create tree for callback
              if UI.TreePush(callback_name) then
                  event_table.settings:draw_bools()

                  if UI.Button("Filter Seen Events") then
                      for i, name in ipairs(event_table.names) do
                          filtered_names[name] = true
                      end
                  end

                  UI.SameLine()
                  if UI.Button("Clear Filter") then
                      filtered_names = {}
                  end

                  if UI.Button("Clear Events") then
                      event_table.events = {}
                      event_table.names = {}
                  end

                  if UI.Button("Update ALL Args") then
                      for k, tbl in pairs(event_table.events) do
                          tbl.settings.bools.wants_args.val = true
                      end
                  end

                  local hide_no_args = event_table.settings:get_bool("hide_no_args")

                  for i, name in ipairs(event_table.names) do
                      if filtered_names[name] == nil then
                          local tbl = event_table.events[name]

                          if not hide_no_args or (hide_no_args and tbl.last_args_count > 0) then
                              draw_tree(name, tbl)
                          end
                      end
                  end

                  UI.TreePop()
              end
          end

          UI.EndWindow()
      end
  end

  return callback_inspector
  ```
* ### Fog of War Example

  ```
  local FogTest = {
      visibilities={},
  }

  local const = {
      MAX_ITERATIONS = 100,
      OUTWARD_MULT = 20,
      RADIUS_STEP = 2,
      BATCH_SIZE = 30,
      BOX_SIZE = 5,
      RADIUS = 0.0,
      R = 255, G = 0, B = 255, A = 255
  }

  function FogTest.OnEntityCreate(ent)
      Log.Write(Entity.GetClassName(ent))
  end

  function FogTest.OnUI()
      if UI.BeginWindow("Test") then
          for k, v in pairs(const) do
              if type(v) == "number" then
                  local changed, value = UI.SliderInt(k, v, 0, 250)

                  if changed and value ~= v then
                      const[k] = value
                      FogTest.reset_points()
                  end
              end
          end

          UI.EndWindow()
      end
  end

  local f_cur = 1
  local i_cur = 1

  function FogTest.for_each_point(func)
      for f=0, const.MAX_ITERATIONS do
          for i=0, 360, const.RADIUS_STEP do
              func(f, i)
          end
      end
  end

  function FogTest.next_point(func)
      for batch=0, const.BATCH_SIZE do
          for i=0, 360, const.RADIUS_STEP do
              func(f_cur, i)
          end

          f_cur = (f_cur + 1) % const.MAX_ITERATIONS
          if f_cur == 0 then break end
      end
  end

  function FogTest.get_radius_point(f, i)
      return Vector(1, 1, 0):Scaled(f * const.OUTWARD_MULT):Rotated(Angle(0, i, 0))
  end

  function FogTest.reset_points()
      f_cur = 0

      FogTest.for_each_point(function(f, i)
          if FogTest.visibilities[f] == nil then
              FogTest.visibilities[f] = {}
          end

          FogTest.visibilities[f][i] = {
              pos = FogTest.get_radius_point(f, i),
              final_pos = Vector(0, 0, 0),
              visible = false,
              screen_pos = { x = 0, y = 0 },
              screen_visible = false
          }
      end)
  end

  FogTest.reset_points()

  local last_pos = Vector(0, 0, 0)

  function FogTest.OnUpdate()
      local me = Heroes.GetLocal()
      if not me then return end

      local me_pos = Input.GetWorldCursorPos()
      me_pos = Vector(math.floor(me_pos:GetX()), math.floor(me_pos:GetY()), math.floor(me_pos:GetZ()))
      last_pos = me_pos

      FogTest.next_point(function(f, i) 
          local visibility = FogTest.visibilities[f][i]
          visibility.final_pos = visibility.pos + me_pos
          visibility.visible = FogOfWar.GetPointVisibility(visibility.final_pos, const.RADIUS)

          if visibility.visible < 1.0 then
              --[[local world_pos = Trace.FindWorld(visibility.final_pos + Vector(0, 0, 1000), visibility.final_pos - Vector(0, 0, 1000))
              if world_pos ~= nil then
                  visibility.final_pos = world_pos
              end]]

              local x, y, visible = Renderer.WorldToScreen(visibility.final_pos)

              visibility.screen_pos = { x = x, y = y }
              visibility.screen_visible = visible
          else
              visibility.screen_visible = false
          end
      end)

  end

  function FogTest.OnDraw()
      local me = Heroes.GetLocal()

      if not me then return end

      FogTest.for_each_point(function(f, i) 
          local visibility = FogTest.visibilities[f][i]

          if visibility.screen_visible then
              Renderer.SetDrawColor(const.R, const.G, const.B, math.floor(const.A * (1 - visibility.visible)))
              Renderer.DrawFilledRect(visibility.screen_pos.x - 2, visibility.screen_pos.y - 2, const.BOX_SIZE + math.floor(f * .25), const.BOX_SIZE + math.floor(f * .25))
          end
      end)

  end

  return FogTest
  ```
* ### Draw names and positions of all neutral camps

  ```
  local test = {}
  local neutral_spawns = {}
  local font = Renderer.LoadFont("Tahoma", 18, 400, 0, 1.0)

  local function fill_spawn_boxes()
      neutral_spawns = {}

      local gamerules_proxy = Entities.Get(1, "C_DOTAGamerulesProxy")

      if gamerules_proxy ~= nil then
          local gamerules = Entity.GetField(gamerules_proxy, "m_pGameRules")

          if gamerules ~= nil then
              local boxes = gamerules.GetField("m_NeutralSpawnBoxes")

              for i, box in ipairs(boxes) do
                  local internal_data = box.GetField("neutralSpawnBoxes")

                  local mins = internal_data.GetField("m_vMinBounds")
                  local maxs = internal_data.GetField("m_vMaxBounds")

                  local center = (mins + maxs):Scaled(0.5)

                  local new_table = {
                      name = box.GetField("strCampName"),
                      pos = center
                  }

                  table.insert(neutral_spawns, new_table)
              end
          end
      end
  end

  function test.OnUpdate()
      if #neutral_spawns == 0 then
          fill_spawn_boxes()
      end
  end

  function test.OnDraw()
      Renderer.SetDrawColor(255, 255, 255, 255)

      for i, spawn in ipairs(neutral_spawns) do
          local x, y, vis = Renderer.WorldToScreen(spawn.pos)

          if vis then
              Renderer.DrawTextCenteredX(font, x, y, spawn.name)
          end
      end
  end

  return test
  ```
* ### Projectile simulation/Hit markers/Hit warnings all-in-one

  Don't use this script to get projectile positions. Use the "Draw all active projectiles" script for that instead.

  ```
  local Projectile = {
      --draw_projectiles = Menu.AddOption({ "Funny" },)
  }

  local projectiles = {}
  local font = Renderer.LoadFont("Tahoma", 24)

  local DOTA_OVERHEAD_ALERT =  {
      OVERHEAD_ALERT_GOLD = 0,
      OVERHEAD_ALERT_DENY = 1,
      OVERHEAD_ALERT_CRITICAL = 2,
      OVERHEAD_ALERT_XP = 3,
      OVERHEAD_ALERT_BONUS_SPELL_DAMAGE = 4,
      OVERHEAD_ALERT_MISS = 5,
      OVERHEAD_ALERT_DAMAGE = 6,
      OVERHEAD_ALERT_EVADE = 7,
      OVERHEAD_ALERT_BLOCK = 8,
      OVERHEAD_ALERT_BONUS_POISON_DAMAGE = 9,
      OVERHEAD_ALERT_HEAL = 10,
      OVERHEAD_ALERT_MANA_ADD = 11,
      OVERHEAD_ALERT_MANA_LOSS = 12,
      OVERHEAD_ALERT_LAST_HIT_EARLY = 13,
      OVERHEAD_ALERT_LAST_HIT_CLOSE = 14,
      OVERHEAD_ALERT_LAST_HIT_MISS = 15,
      OVERHEAD_ALERT_MAGICAL_BLOCK = 16,
      OVERHEAD_ALERT_INCOMING_DAMAGE = 17,
      OVERHEAD_ALERT_OUTGOING_DAMAGE = 18,
      OVERHEAD_ALERT_DISABLE_RESIST = 19,
      OVERHEAD_ALERT_DEATH = 20,
      OVERHEAD_ALERT_BLOCKED = 21,
      inverse = {}
  }

  for k, v in pairs(DOTA_OVERHEAD_ALERT) do
      DOTA_OVERHEAD_ALERT.inverse[v] = k
  end

  local last_hit_enemy = nil
  local last_attacking_enemy = nil

  function Projectile.OnProjectile(p)
      if p.source == nil then return end
      if p.target == nil then return end

      table.insert(projectiles, {
          start = NPC.GetAttachmentByIndex(p.source, p.sourceAttachment),
          source = p.source,
          target = p.target,
          speed = p.moveSpeed,
          is_attack = p.isAttack,
          is_evaded = p.isEvaded,
          t = p.launchTick * (1/30),
          attach = p.sourceAttachment,
          should_draw = false,
          current_position = Vector(0, 0, 0),
          current_velocity = Vector(0, 0, 0),
          has_set_velocity = false,
          prev_positions = {}
      })

      if p.target == Heroes.GetLocal() and Entity.GetTeamNum(p.source) ~= Entity.GetTeamNum(p.target) then
          last_attacking_enemy = p.source
          Engine.ExecuteCommand("snd_sos_start_soundevent xray.beep")
      end
  end

  local function round(num, numDecimalPlaces)
        local mult = 10^(numDecimalPlaces or 0)
        return math.floor(num * mult + 0.5) / mult
  end

  local function to_ticks(time, tick_rate)
      return round(0.5 + time * tick_rate, 1)
  end

  -- only for updating projectile start position
  function Projectile.OnUpdate()
      local cur_time = Entity.GetField(Heroes.GetLocal(), "m_flAnimTime")

      for i, p in ipairs(projectiles) do
          local cur_time_ticks = to_ticks(cur_time, 60)
          local t_ticks = to_ticks(p.t, 60)

          local is_delayed = cur_time_ticks <= t_ticks

          if not Entity.IsEntity(p.source) or not Entity.IsEntity(p.target) then
              table.remove(projectiles, i)
          -- keep updating the projectile start position until the true time (projectile.launchTick) is reached
          elseif is_delayed then
              p.start = NPC.GetAttachmentByIndex(p.source, p.attach)
              p.should_draw = cur_time_ticks >= t_ticks
          else
              p.should_draw = cur_time_ticks >= t_ticks
          end
      end
  end

  local function lerp_vec(vec, target_vec, t)
      return vec:Scaled(t) + target_vec:Scaled(1 - t)
  end

  local last_gametime = 0
  local last_clock = os.clock()
  local last_accurate_time = 0
  local accumulated_time = 0
  local host_timescale = CVar.FindVar("host_timescale")

  local snd_list = {
      --"sounds/ui/tutorial_ui_click_01.vsnd",
      --"sounds/ui/ui_xp_click_01.vsnd_c",
      "sounds/physics/damage/building/damage01"
  }

  local bad_snds = {
      --"sounds/ui/ui_ability_declick_01.vsnd",
      --"sounds/ui/ui_declick_simple_01.vsnd_c",
      "BUTTON_CLICK_MINOR"
  }

  local function select_from_table(t, i)
      return t[math.random(1, #t)]
  end

  function Projectile.OnOverheadEvent(event)
      if event.sourcePlayer ~= Players.GetLocal() then return end

      if event.type == DOTA_OVERHEAD_ALERT.OVERHEAD_ALERT_INCOMING_DAMAGE then
          last_attacking_enemy = Entity.GetField(event.targetPlayer, "m_hAssignedHero")

          Engine.ExecuteCommand("snd_sos_start_soundevent" .. " " .. select_from_table(bad_snds, i))
      elseif event.type == DOTA_OVERHEAD_ALERT.OVERHEAD_ALERT_OUTGOING_DAMAGE then
          last_hit_enemy = event.target

          Audio.PlaySound(select_from_table(snd_list, i), 0.5)
      elseif event.type == DOTA_OVERHEAD_ALERT.OVERHEAD_ALERT_MISS then
          Engine.ExecuteCommand("snd_sos_start_soundevent SeasonalConsumable.TI9.Shovel.PudglingFart")
      else
          Alerts.Add(DOTA_OVERHEAD_ALERT.inverse[event.type] .. " - > " .. tostring(event.value))
      end
  end

  function Projectile.OnStartSound(sound)
      if (sound.source == Heroes.GetLocal() or sound.source == last_hit_enemy or sound.source == last_attacking_enemy) and 
         (string.find(sound.name, "Attack") or string.find(sound.name, "attack")) then
          --Alerts.Add(sound.name)

          Engine.ExecuteCommand("snd_sos_stop_soundevent_guid " .. tostring(sound.guid))

          if sound.source == last_hit_enemy then
              last_hit_enemy = nil
          end

          if sound.source == last_attacking_enemy then
              last_hit_enemy = nil
          end
      end
  end

  function Projectile.OnDraw()
      local me = Heroes.GetLocal()
      if me == nil then return end

      -- A way to get the current time. projectile.launchTick is not the same as GameRules.GetGameTime()   
      local cur_time = Entity.GetField(me, "m_flAnimTime")

      local timescale = CVar.GetVarFloat(host_timescale)

      -- makes it look nicer at higher FPS limits
      if cur_time == last_gametime and not GameRules.IsPaused() then
          accumulated_time = accumulated_time + ((os.clock() - last_clock) * timescale)
      else
          accumulated_time = 0
      end

      local accurate_time = cur_time + accumulated_time
      local delta_frame = os.clock() - last_clock
      local delta_tick = cur_time - last_gametime

      last_accurate_time = accurate_time
      last_gametime = cur_time
      last_clock = os.clock()

      math.randomseed(math.random(1, 100) + os.time())

      for i=1, #projectiles do
          local p = projectiles[i]

          if p ~= nil and (not Entity.IsEntity(p.source) or not Entity.IsEntity(p.target)) then
              table.remove(projectiles, i)
          elseif p ~= nil and p.should_draw then
              local target_absorigin = Entity.GetAbsOrigin(p.target)
              local target_pos = NPC.GetAttachment(p.target, "attach_hitloc")

              -- this is where the projectile is traveling to
              local dir = (target_pos - p.start):Normalized()

              local wanted_dir = (target_pos - p.current_position):Normalized()
              local wanted_velocity = wanted_dir:Scaled(p.speed)

              if not p.has_set_velocity then
                  if p.target == me then
                      --Engine.ExecuteCommand("snd_sos_start_soundevent xray.beep")
                  end

                  -- Start it forward 1 tick.
                  p.current_position = p.start + dir:Scaled((accurate_time - p.t) * p.speed)

                  -- set it with proper values
                  wanted_dir = (target_pos - p.current_position):Normalized()
                  wanted_velocity = wanted_dir:Scaled(p.speed)

                  p.current_velocity = wanted_velocity
                  p.has_set_velocity = true
              else
                  p.current_velocity = lerp_vec(p.current_velocity, wanted_velocity, delta_frame * timescale)
                  p.current_position = p.current_position + p.current_velocity:Scaled(delta_frame * timescale)
              end

              table.insert(p.prev_positions, p.current_position)

              local x, y, visible = Renderer.WorldToScreen(p.current_position)

              if visible then
                  Renderer.SetDrawColor(255, 0, 0, 255)
                  Renderer.DrawFilledRect(x - 10, y - 10, 20, 20)

                  local prev_prev = p.start

                  for k, prev in ipairs(p.prev_positions) do
                      local px, py, pvis = Renderer.WorldToScreen(prev)
                      local px2, py2, pvis2 = Renderer.WorldToScreen(prev_prev)

                      Renderer.DrawLine(px, py, px2, py2)

                      prev_prev = prev
                  end

                  if #p.prev_positions > 100 then
                      table.remove(p.prev_positions, 1)
                  end
              end

              local distance_to_unit = (target_pos - p.current_position):Length2D()

              if not Entity.IsAlive(p.target) or distance_to_unit <= NPC.GetProjectileCollisionSize(p.target) + Entity.GetField(p.target, "m_flCollisionPadding") then
                  -- HITMARKERS
                  if p.target == me then
                      ---Audio.PlaySound(select_from_table(bad_snds, i))
                  end

                  if p.source == me then
                      if p.is_attack then
                          --Audio.PlaySound(select_from_table(snd_list, i))
                          Engine.ExecuteCommand("clear")
                      else
                          Audio.PlaySound("sounds/ui/tower_callout.vsnd")
                          Engine.ExecuteCommand("clear")
                      end
                  end

                  table.remove(projectiles, i)
                  if i > 1 then
                      i = i - 1

                      if i > #projectiles then break end
                  end
              end
          end
      end
  end

  return Projectile
  ```
* ### Bad manners on death, Mimic enemy chat

  ```
  local ChatTest = {}

  ChatTest.whatToSay = { "xd", "Xd", "XD", "xD", "?" }

  function ChatTest.OnChatEvent(chatEvent)
      --[[Log.Write("Chat event")

      Log.Write(" Type: " .. chatEvent.type)
      Log.Write(" value: " .. chatEvent.value)]]

      -- hero killed event type
      if chatEvent.type ~= 0 then return end

      local source = nil
      local target = nil

      for i = 1, Heroes.Count() do
          local hero = Heroes.Get(i)
          local playerID = Hero.GetPlayerID(hero)

          --Log.Write(i .. playerID)

          if chatEvent.players[2] == playerID then source = hero
          elseif chatEvent.players[1] == playerID then target = hero end
      end

      if not source or not target then return end

      --Log.Write(NPC.GetUnitName(source) .. " killed " .. NPC.GetUnitName(target))

      local myHero = Heroes.GetLocal()

      if Entity.IsSameTeam(myHero, source) and not Entity.IsSameTeam(myHero, target) then
          local choice = ChatTest.whatToSay[math.random(1, #ChatTest.whatToSay)]

          Engine.ExecuteCommand("say " .. choice)
      end
  end

  function ChatTest.OnSayText(textEvent)
      local myPlayer = Players.GetLocal()
      if not myPlayer then return end

      if not textEvent.entity then return end
      if Entity.IsSameTeam(myPlayer, textEvent.entity) then return end

      local text = ""

      for i = 1, string.len(textEvent.params[2]) do
          local c = textEvent.params[2]:sub(i, i)

          if (math.random(0, 1) == 0) then
              text = text .. string.lower(c)
          else
              text = text .. string.upper(c)
          end
      end

      Engine.ExecuteCommand("say \"" .. text .. " " .. ChatTest.whatToSay[math.random(1, #ChatTest.whatToSay)] .. "\"")
  end

  return ChatTest
  ```
* ### Raycast tester

  ```
  local raycast = {}

  local const = {
      target_team = Enum.TeamType.TEAM_BOTH,
      target_flags = Enum.TargetType.DOTA_UNIT_TARGET_ALL | Enum.TargetType.DOTA_UNIT_TARGET_TREE,
      scan_width = 100,
      scan_height = 1000,
      projectile_width = 100,
      forward_offset = 0,
      z_offset = 5,
      PULSE_MIN = 100,
      PULSE_MAX = 255
  }

  local font = Renderer.LoadFont("Tahoma", 24)

  local const_names = {}

  for k, v in pairs(const) do
      table.insert(const_names, k)
  end

  table.sort(const_names)

  function raycast.OnUI()
      if UI.BeginWindow("Test") then
          for i, k in ipairs(const_names) do
              local v = const[k]
              --Chat.Print(Chat.GetChannels()[1], k .. " = " ..  tostring(v))
              local changed, value

              if type(v) == "number" then
                  changed, value = UI.SliderInt(k, v, -120, 120)

                  local changed2, value2 = UI.Textbox(k, tostring(value), "1")

                  if (not changed) and changed2 and tonumber(value2) ~= nil then
                      changed = changed2
                      value = tonumber(value2)
                  end
              elseif type(v) == "boolean" then
                  changed, value = UI.Checkbox(k, v)
              end

              if changed and value ~= v then 
                  const[k] = value
              end
          end

          local function make_labels_for_enum(value, enum)
              local n = 1

              for k, v in pairs(enum) do
                  local result = (value & enum[k])

                  if result ~= 0 and result == enum[k] then
                      UI.Label(k)
                      n = n + 1
                  end
              end

              return n
          end

          local function same_line_n(n) 
              for i=1, n do
                  UI.SameLine()
              end
          end

          local n = make_labels_for_enum(const.target_flags, Enum.TargetType)
          make_labels_for_enum(const.target_team, Enum.TargetTeam)

          UI.EndWindow()
      end
  end

  local hit_entities = {}
  local pulse = 0
  local pulse_direction = 1

  local function trace_from_entity(ent)
      if hit_entities[ent] ~= nil then return end
      hit_entities[ent] = true

      local rot = Entity.GetAbsRotation(ent)
      local cursor_pos = Input.GetWorldCursorPos()
      local this_ent_pos = Entity.GetAbsOrigin(ent)

      local forward = (cursor_pos - this_ent_pos):Normalized()
      forward:SetZ(0)
      forward:Normalize()

      local right = forward:Cross(Vector(0, 0, 1))

      local ray_start = this_ent_pos + forward:Scaled(const.forward_offset) + Vector(0, 0, const.z_offset)
      local ray_end = ray_start + forward:Scaled(8192.0)

      local lines = {}

      local function insert_line(pos)
          local e = {}
          e.vec = pos
          e.x, e.y, e.visible = Renderer.WorldToScreen(e.vec)
          table.insert(lines, e)
      end

      insert_line(ray_start + right:Scaled(const.scan_width * -1))
      insert_line(ray_start + forward:Scaled(2000.0) + right:Scaled(const.scan_width * -1))

      insert_line(ray_start + right:Scaled(const.scan_width))
      insert_line(ray_start + forward:Scaled(2000.0) + right:Scaled(const.scan_width))

      Renderer.SetDrawColor(0, 255, 0, 255)

      for i=1, #lines, 2 do
          --line start, line end
          local ls = lines[i]
          local le = lines[i+1]

          Renderer.DrawLine(ls.x, ls.y, le.x, le.y)
      end

      local ent_team = Entity.GetTeamNum(ent)

      ---------------------------------------------------------------------------------
      -- Cast a 2D box from ray_start to ray_end and collect all entities along the way
      ---------------------------------------------------------------------------------
      local entities = 
       Trace.FindEntities(
          ray_start, 
          ray_end,
          const.scan_width,
          const.scan_height,
          ent_team, 
          const.target_team, 
          const.target_flags, 
          -- our custom predicate for FindEntities
          function (entity)
              --if not Entity.IsNPC(entity) then return false end
              if entity == ent then return false end

              local ent_position = Entity.GetAbsOrigin(entity)
              --local attach_position = NPC.GetAttachment(entity, "attach_hitloc")

              local delta_to_ent = ent_position - ray_start

              local distance_to_ray = (ent_position - ray_start):Length2D()
              --local ray_position = ray_start + forward:Scaled(distance_to_ray)
              local ray_position = ray_start + delta_to_ent:Project(forward)

              --[[local x, y, vis = Renderer.WorldToScreen(ray_position)

              if vis then
                  Renderer.DrawFilledRect(x, y, 10, 10)
              end]]

              local collision_size = Entity.IsNPC(entity) and NPC.GetProjectileCollisionSize(entity) or 0

              local width = const.scan_width + collision_size

              local result = (ray_position - ent_position):Length2D() < width

              return result
          end)

      if entities == nil or #entities == 0 then return end

      table.sort(entities, function(a, b)
          local a_origin = Entity.GetAbsOrigin(a)
          local b_origin = Entity.GetAbsOrigin(b)

          return (a_origin - ray_start):Length2D() < (b_origin - ray_start):Length2D()
      end)

      for i=1, #entities do
          local entity = entities[i]
          local ent_position = Entity.GetAbsOrigin(entity)
          local distance = (ent_position - ray_start):Length2D()

          local x_start, y_start, start_visible = Renderer.WorldToScreen(ray_start)
          local x_end, y_end, end_visible = Renderer.WorldToScreen(ray_start + forward:Scaled(distance))

          local bottom_x, bottom_y, bottom_visible = Renderer.WorldToScreen(ent_position)
          local ent_x, ent_y, ent_visible = Renderer.WorldToScreen(ent_position + Vector(0, 0, 100))

          if start_visible and end_visible then
              Renderer.SetDrawColor(math.floor(255 * (i / #entities)), 255, 0, 255)
              Renderer.DrawLine(x_start, y_start, x_end, y_end)

              local angle = Entity.GetRotationToEntity(ent, entity)

              if i == 1 then
                  Renderer.SetDrawColor(0, 255, 0, 255)
                  Renderer.DrawFilledRect(ent_x - 10, ent_y, 20, 20)
              else
                  Renderer.SetDrawColor(0, 0, 255, pulse)
                  Renderer.DrawFilledRect(ent_x - 10, ent_y, 20, 20)
              end

              Renderer.SetDrawColor(0, 0, 255, 255)
              Renderer.DrawTextCenteredX(font, ent_x, ent_y, tostring(angle:GetYaw()))
          end

          ray_start = ray_start + forward:Scaled(distance)
      end

      pulse = pulse + (pulse_direction * 10)

      if pulse >= const.PULSE_MAX or pulse <= const.PULSE_MIN then
          pulse = pulse >= const.PULSE_MAX and const.PULSE_MAX or const.PULSE_MIN
          pulse_direction = pulse_direction * -1

          --Log.Write(pulse)
      end
  end

  function raycast.OnDraw()
      local me = Heroes.GetLocal()
      if me == nil then return end

      trace_from_entity(me)
      hit_entities = {}
  end

  return raycast
  ```
