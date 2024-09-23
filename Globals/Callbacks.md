# Callbacks

Top-level scripts (those that reside in the `/scripts/`​ directory) are expected to return a table. If the table that gets returned contains any of the following functions then those functions will automatically be registered as callbacks and be called at the appropriate time.

---

* [OnChatEvent](https://hake.me/docs/globals/callbacks#onchatevent-chatevent)
* [OnCustomGameEvent](https://hake.me/docs/globals/callbacks#oncustomgameevent-event)
* [OnDraw](https://hake.me/docs/globals/callbacks#ondraw)
* [OnEntityCreate](https://hake.me/docs/globals/callbacks#onentitycreate-ent)
* [OnEntityDestroy](https://hake.me/docs/globals/callbacks#onentitydestroy-ent)
* [OnGameEnd](https://hake.me/docs/globals/callbacks#ongameend)
* [OnGameStart](https://hake.me/docs/globals/callbacks#ongamestart)
* [OnGameEvent](https://hake.me/docs/globals/callbacks#ongameevent-event)
* [OnGCMessageReceived](https://hake.me/docs/globals/callbacks#ongcmessagereceived-msg)
* [OnGCMessageSend](https://hake.me/docs/globals/callbacks#ongcmessagesend-msg)
* [OnGCSharedObjectUpdated](https://hake.me/docs/globals/callbacks#ongcsharedobjectupdated-msg)
* [OnLinearProjectileCreate](https://hake.me/docs/globals/callbacks#onlinearprojectilecreate-projectile)
* [OnLinearProjectileDestroy](https://hake.me/docs/globals/callbacks#onlinearprojectiledestroy-projectile)
* [OnMenuOptionChange](https://hake.me/docs/globals/callbacks#onmenuoptionchange-option-oldvalue-newvalue)
* [OnModifierGained](https://hake.me/docs/globals/callbacks#onmodifiergained-npc-modifier)
* [OnModifierLost](https://hake.me/docs/globals/callbacks#onmodifierlost-npc-modifier)
* [OnNetMessageReceived](https://hake.me/docs/globals/callbacks#onnetmessagereceived-msg)
* [OnNetMessageSend](https://hake.me/docs/globals/callbacks#onnetmessagesend-msg)
* [OnOverheadEvent](https://hake.me/docs/globals/callbacks#onoverheadevent-event)
* [OnPanoramaUIEvent](https://hake.me/docs/globals/callbacks#onpanoramauievent-event)
* [OnParticleCreate](https://hake.me/docs/globals/callbacks#onparticlecreate-particle)
* [OnParticleDestroy](https://hake.me/docs/globals/callbacks#onparticledestroy-particle)
* [OnParticleSetText](https://hake.me/docs/globals/callbacks#onparticlesettext-particle)
* [OnParticleUpdateEntity](https://hake.me/docs/globals/callbacks#onparticleupdateentity-particle)
* [OnParticleUpdate](https://hake.me/docs/globals/callbacks#onparticleupdate-particle)
* [OnPreUpdate](https://hake.me/docs/globals/callbacks#onpreupdate)
* [OnPrepareUnitOrders](https://hake.me/docs/globals/callbacks#onprepareunitorders-orders)
* [OnProjectileLoc](https://hake.me/docs/globals/callbacks#onprojectileloc-projectile)
* [OnProjectile](https://hake.me/docs/globals/callbacks#onprojectile-projectile)
* [OnSayText](https://hake.me/docs/globals/callbacks#onsaytext-textevent)
* [OnScriptLoad](https://hake.me/docs/globals/callbacks#onscriptload)
* [OnScriptUnload](https://hake.me/docs/globals/callbacks#onscriptunload)
* [OnStartSound](https://hake.me/docs/globals/callbacks#onstartsound-sound)
* [OnUnitAnimationEnd](https://hake.me/docs/globals/callbacks#onunitanimationend-animation)
* [OnUnitAnimation](https://hake.me/docs/globals/callbacks#onunitanimation-animation)
* [OnUpdate](https://hake.me/docs/globals/callbacks#onupdate)
* [OnUserSay](https://hake.me/docs/globals/callbacks#onusersay-info)

---

## `OnChatEvent(chatEvent)`​

### Arguments

* ​`chatEvent`​ - A table containing the following fields:

  * ​`type`​ - A number. See [Protobuf enum value](https://github.com/SteamDatabase/Protobufs/blob/master/dota2/dota_usermessages.proto#L149)
  * ​`value`​
  * ​`players`​ - An array containing a maximum of 6 player IDs this event applies to.

### Remarks

This callback does not capture players' chat messages. Use `OnSayText`​ for capturing text events.

---

## `OnCustomGameEvent(event)`​

### Arguments

* ​`event`​ - A table containing the following fields:

  * ​`name`​ - The name of the event
  * ​`data`​ - A table of addon-specific key : values

---

## `OnDraw()`​

### Remarks

This callback gets called when its time for the script to issue draw commands. Draw commands are issued by `Renderer`​'s functions and most will only work when called within an `OnDraw()`​ callback. Exceptions to this are `Renderer`​'s `LoadFont(...)`​ function which will work anywhere.

Note that `OnDraw()`​ callbacks are only called at a fixed \~30FPS and are not optimal for implementing feature logic. This callback should only be used to draw things.

---

## `OnEntityCreate(ent)`​

### Arguments

* ​`ent`​ - The entity that was created.

---

## `OnEntityDestroy(ent)`​

### Arguments

* ​`ent`​ - The entity thats been destroyed.

---

## `OnGameEnd()`​

### Remarks

Called when the game ends or the local player leaves a game.

---

## `OnGameStart()`​

### Remarks

Called when the game begins or the local player joins a game. Both the local player and local hero are available when this callback gets invoked.

---

## `OnGameEvent(event)`​

A developer tool for inspecting this event can be found here: [callback_inspector.lua](https://hake.me/forums/attachments/callback_inspector-lua.5740/)

### Arguments

* ​`event`​
* ​`name`​ - name of the event, e.g. "entity\_hurt"
* ​`data`​ - table

### Remarks

* Requires manually listening to some events, e.g.

  * ​`GameEvents.StartListening("entity_hurt")`​
* Possible events can be found in `resource/game.gameevents`​ and some others

  * Or you can use `OnNetMessageReceived(msg)`​ where `msg.name == "CMsgSource1LegacyGameEventList"`​

---

## `OnGCMessageReceived(msg)`​

### Arguments

* ​`msg`​ - A table containing the following fields:

  * ​`name`​ - The enum name of the message
  * ​`type`​ - Type index of the message
  * ​`GetArguments()`​ - A function

    * Calling this returns the arguments for this message, as a table
    * There is a **LARGE** (\~1 second) performance impact the first time this is called per unique message (it only happens once per message type)

### Remarks

Triggers when a message has been received from the Game Coordinator.

​`GetArguments()`​ also contains `msg_hdr`​ field. See [GCClient.SendMessage](https://hake.me/docs/systems/gcclient#gcclient-sendmessage-protobuf-msgtype-job_id)

---

## `OnGCMessageSend(msg)`​

### Arguments

* ​`msg`​ - A table containing the following fields:

  * ​`name`​ - The enum name of the message
  * ​`type`​ - Type index of the message
  * ​`GetArguments()`​ - A function

    * Calling this returns the arguments for this message, as a table
    * There is a **LARGE** (\~1 second) performance impact the first time this is called per unique message (it only happens once per message type)

### Remarks

Triggers when a message is going to be sent to the Game Coordinator. Return `false`​ to discard the message.

​`GetArguments()`​ also contains `msg_hdr`​ field. See [GCClient.SendMessage](https://hake.me/docs/systems/gcclient#gcclient-sendmessage-protobuf-msgtype-job_id)

---

## `OnGCSharedObjectUpdated(msg)`​

A developer tool for inspecting this event can be found here: [callback_inspector.lua](https://hake.me/forums/attachments/callback_inspector-lua.5740/)

### Arguments

* ​`msg`​ - A table containing the following fields:

  * ​`name`​ - The name of the event
  * ​`GetArguments()`​ - A function

    * Calling this returns the arguments for this message, as a table

### Remarks

* Triggers when a Game Coordinator SharedObject is created or updated, e.g.

  * ​`CSODOTALobby`​
  * ​`CSODOTAParty`​
  * etc...

---

## `OnLinearProjectileCreate(projectile)`​

### Arguments

* ​`projectile`​ - A table with the following fields:

  * ​`source`​ - The entity that is going to create this projectile.
  * ​`origin`​ - Start position of this projectile.
  * ​`velocity`​ - Vector.
  * ​`particleIndex`​ - 64-bit hash of the projectile name. May be useful for caching.
  * ​`handle`​ - Unique handle to keep track of this projectile.
  * ​`acceleration`​
  * ​`latency`​
  * ​`maxSpeed`​
  * ​`fullName`​
  * ​`name`​

---

## `OnLinearProjectileDestroy(projectile)`​

### Arguments

* ​`projectile`​ - A table with the following fields:

  * ​`handle`​

---

## `OnMenuOptionChange(option, oldValue, newValue)`​

### Remarks

Called whenever a menu option is changed.

---

## `OnModifierGained(npc, modifier)`​

### Arguments

* ​`npc`​ - The NPC that gained this modifier.
* ​`modifier`​ - The modifier that was gained. Use the [Modifier](https://hake.me/docs/systems/modifier) table.

### Remarks

Called when an NPC gains a modifier.

---

## `OnModifierLost(npc, modifier)`​

### Arguments

* ​`npc`​ - The NPC that lost this modifier.
* ​`modifier`​ - The modifier that was lost. Use the [Modifier](https://hake.me/docs/systems/modifier) table.

### Remarks

Called when an NPC loses a modifier. The modifier is still valid at this point and can be used with the [Modifier](https://hake.me/docs/systems/modifier) table.

---

## `OnNetMessageReceived(msg)`​

A developer tool for inspecting this event can be found here: [callback_inspector.lua](https://hake.me/forums/attachments/callback_inspector-lua.5740/)

### Arguments

* ​`msg`​ - A table containing the following fields:

  * ​`name`​ - The name of the event
  * ​`GetArguments()`​ - A function

    * Calling this returns the arguments for this message, as a table
    * There is a (small) performance impact with this, so it should NOT be called for every message, only for the message you need

      * It should also only be called once per message, store it in a variable to minimize performance impact

### Remarks

* Triggers when a protobuf packet was received from the server
* Many of our existing callbacks can be recreated with this callback (e.g. `OnPrepareUnitOrders`​, `OnParticleCreate`​)
* **DOES NOT WORK FOR GAME COORDINATOR MESSAGES!**

---

## `OnNetMessageSend(msg)`​

A developer tool for inspecting this event can be found here: [callback_inspector.lua](https://hake.me/forums/attachments/callback_inspector-lua.5740/)

### Arguments

* ​`msg`​ - A table containing the following fields:

  * ​`name`​ - The name of the event
  * ​`GetArguments()`​ - A function

    * Calling this returns the arguments for this message, as a table
    * There is a (small) performance impact with this, so it should NOT be called for every message, only for the message you need

      * It should also only be called once per message, store it in a variable to minimize performance impact

### Remarks

* Triggers when a protobuf packet is going to be sent to the server
* **DOES NOT WORK FOR GAME COORDINATOR MESSAGES!**

---

## `OnOverheadEvent(event)`​

### Arguments

* ​`event`​

  * ​`type`​ - See `DOTA_OVERHEAD_ALERT`​ below
  * ​`value`​ - int
  * ​`sourcePlayer`​ - Entity
  * ​`targetPlayer`​ - Entity
  * ​`target`​ - Entity

### Remarks

Fires when a value needs to be displayed above a unit.

```
enum DOTA_OVERHEAD_ALERT {
    OVERHEAD_ALERT_GOLD = 0;
    OVERHEAD_ALERT_DENY = 1;
    OVERHEAD_ALERT_CRITICAL = 2;
    OVERHEAD_ALERT_XP = 3;
    OVERHEAD_ALERT_BONUS_SPELL_DAMAGE = 4;
    OVERHEAD_ALERT_MISS = 5;
    OVERHEAD_ALERT_DAMAGE = 6;
    OVERHEAD_ALERT_EVADE = 7;
    OVERHEAD_ALERT_BLOCK = 8;
    OVERHEAD_ALERT_BONUS_POISON_DAMAGE = 9;
    OVERHEAD_ALERT_HEAL = 10;
    OVERHEAD_ALERT_MANA_ADD = 11;
    OVERHEAD_ALERT_MANA_LOSS = 12;
    OVERHEAD_ALERT_LAST_HIT_EARLY = 13;
    OVERHEAD_ALERT_LAST_HIT_CLOSE = 14;
    OVERHEAD_ALERT_LAST_HIT_MISS = 15;
    OVERHEAD_ALERT_MAGICAL_BLOCK = 16;
    OVERHEAD_ALERT_INCOMING_DAMAGE = 17;
    OVERHEAD_ALERT_OUTGOING_DAMAGE = 18;
    OVERHEAD_ALERT_DISABLE_RESIST = 19;
    OVERHEAD_ALERT_DEATH = 20;
    OVERHEAD_ALERT_BLOCKED = 21;
}
```

---

## `OnPanoramaUIEvent(event)`​

A developer tool for inspecting this event can be found here: ~~[panorama.lua](https://hake.me/forums/attachments/panorama-lua.4860/)~~ [callback_inspector.lua](https://hake.me/forums/attachments/callback_inspector-lua.5740/)

### Arguments

* ​`event`​ - A table containing the following fields:

  * ​`name`​ - The name of the event
  * ​`GetArguments()`​ - A function

    * Calling this returns the arguments for this event, as a table
    * There is a performance impact with this, so it should NOT be called for every event, only for the events you need

      * It should also only be called once per event, store it in a variable to minimize performance impact
    * If `arguments[1]`​ is a table, it is usually the panel associated with the event

### Remarks

* Triggers when an event is dispatched by the Panorama UI
* Can be used to gather information about the state of the UI
* **Must return a boolean**

  * Returning `true`​ will let the game process the event
  * Returning `false`​ will stop the game from processing the event

    * e.g. returning `false`​ for `DOTAChatTextSubmitted`​ will not let the user type a chat message

### Examples

Checking if the shop is open:

```
function PanoramaUITest.OnPanoramaUIEvent(event)
    if event.name == "DOTAHUDShopOpened" then
        Log.Write("Shop opened")
    elseif event.name == "DOTAHUDShopClosed" then
        Log.Write("Shop closed")
    end

    -- Return true to let the game process the event
    return true
end
```

---

## `OnParticleCreate(particle)`​

### Arguments

* ​`particle`​ - A table with the following fields:

  * ​`index`​ - Unique index to keep track of this particle for future uses, such as `OnParticleUpdate`​
  * ​`entity`​ - *can be nil*
  * ​`particleNameIndex`​ - 64-bit hash of the particle name.
  * ​`attachType`​
  * ​`entityForModifiers`​ - *can be nil*
  * ​`fullName`​
  * ​`name`​

---

## `OnParticleDestroy(particle)`​

### Arguments

* ​`particle`​ - A table with the following fields:

  * ​`index`​
  * ​`destroyImmediately`​

---

## `OnParticleSetText(particle)`​

### Arguments

* ​`particle`​ - A table with the following fields:

  * ​`index`​
  * ​`text`​

---

## `OnParticleUpdate(particle)`​

### Arguments

* ​`particle`​ - A table with the following fields:

  * ​`index`​
  * ​`position`​
  * ​`controlPoint`​

---

## `OnParticleUpdateEntity(particle)`​

### Arguments

* ​`particle`​ - A table with the following fields:

  * ​`index`​
  * ​`controlPoint`​
  * ​`entity`​ - Entity that this particle is attaching to.
  * ​`attachType`​
  * ​`attachment`​
  * ​`position`​ - Fallback position for this particle (can be used to get fog position).
  * ​`includeWearables`​

---

## `OnPreUpdate()`​

### Remarks

This callback gets called prior to the game updating its state based on the latest information the client has received.

---

## `OnPrepareUnitOrders(orders)`​

### Arguments

* ​`orders`​ - A table with the following fields:

  * ​`player`​
  * ​`order`​ - See `Enums.UnitOrder`​.
  * ​`target`​
  * ​`position`​
  * ​`ability`​
  * ​`orderIssuer`​ - See `Enums.PlayerOrderIssuer`​.
  * ​`npc`​
  * ​`queue`​
  * ​`showEffects`​

### Returns

Boolean, `true`​ if the orders should go through, `false`​ if the orders should not go through.

### Remarks

This callback should return `true`​ by default and only return `false`​ when you specifically do not want the orders to go through.

---

## `OnProjectile(projectile)`​

### Arguments

* ​`projectile`​ - A table with the following fields:

  * ​`source`​ - The entity that is going to create this projectile.
  * ​`target`​ - The target entity.
  * ​`targetLoc`​ - The target location this projectile (can) heads towards.
  * ​`moveSpeed`​ - Speed of this projectile.
  * ​`sourceAttachment`​ - Bone attachment index of the source entity that this projectile is fired from.
  * ​`particleSystemHandle`​ - 64-bit hash of the projectile name. May be useful for caching.
  * ​`dodgeable`​
  * ​`isAttack`​
  * ​`isEvaded`​
  * ​`expireTime`​
  * ​`maxImpactTime`​
  * ​`colorGemColor`​
  * ​`fullName`​
  * ​`name`​
  * ​`launchTick`​
  * ​`handle`​

---

## `OnProjectileLoc(projectile)`​

### Arguments

* ​`projectile`​ - A table with the following fields:

  * ​`sourceLoc`​ - The source location this projectile originates from.
  * ​`targetLoc`​ - The target location this projectile (can) heads towards.
  * ​`target`​ - The target entity.
  * ​`moveSpeed`​ - Speed of this projectile.
  * ​`sourceAttachment`​ - Bone attachment index of the source entity that this projectile is fired from.
  * ​`particleSystemHandle`​ - 64-bit hash of the projectile name. May be useful for caching.
  * ​`dodgeable`​
  * ​`isAttack`​
  * ​`isEvaded`​
  * ​`expireTime`​
  * ​`maxImpactTime`​
  * ​`colorGemColor`​
  * ​`fullName`​
  * ​`name`​
  * ​`launchTick`​
  * ​`handle`​

---

## `OnSayText(textEvent)`​

### Arguments

* ​`textEvent`​ - A table containing the following fields:

  * ​`entity`​ - The entity this chat message originated from (usually a player)
  * ​`chat`​ - Boolean. Unknown what it is for at this time.
  * ​`messageName`​ - A string detailing the message type.
  * ​`params`​ - An array containing the following string fields:

    * ​`params[1]`​ - The name of the player/NPC that sent this message.
    * ​`params[2]`​ - The text message that was sent.
    * ​`params[3]`​ - Unknown at this time.
    * ​`params[4]`​ - Unknown at this time.

---

## `OnScriptLoad()`​

### Remarks

Called when the script is loaded.

---

## `OnScriptUnload()`​

### Remarks

Called when the script is unloaded.

---

## `OnStartSound(sound)`​

### Arguments

* ​`sound`​ - A table containing the following fields:

  * ​`source`​ - The entity the sound originates from
  * ​`name`​
  * ​`hash`​
  * ​`guid`​
  * ​`seed`​
  * ​`position`​ - Position the sound originates from

---

## `OnUnitAnimation(animation)`​

### Arguments

* ​`animation`​ - A table with the following fields:

  * ​`unit`​
  * ​`sequenceVariant`​
  * ​`playbackRate`​
  * ​`castpoint`​
  * ​`type`​
  * ​`activity`​
  * ​`sequence`​
  * ​`sequenceName`​

### Remarks

This callback gets called whenever an animation starts.

---

## `OnUnitAnimationEnd(animation)`​

### Arguments

* ​`animation`​ - A table with the following fields:

  * ​`unit`​
  * ​`snap`​

---

## `OnUpdate()`​

### Remarks

This callback gets called after the game has updated its state based on the latest information the client has received. It is also the most appropriate place for implementing most feature logic.

---

## `OnUserSay(info)`​

### Arguments

* ​`info`​ - A table with the following fields:

  * ​`channel`​
  * ​`msg`​

### Remarks

Should return a boolean, `false`​ if the message should not go through, `true`​ otherwise.
