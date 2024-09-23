# Entity

This table contains functions that work on entities.

* [Entity.IsSameTeam](https://hake.me/docs/entities/entity#entity-issameteam-ent-ent2)
* [Entity.IsEntity](https://hake.me/docs/entities/entity#entity-isentity-ent)
* [Entity.IsNPC](https://hake.me/docs/entities/entity#entity-isnpc-ent)
* [Entity.IsHero](https://hake.me/docs/entities/entity#entity-ishero-ent)
* [Entity.IsPlayer](https://hake.me/docs/entities/entity#entity-isplayer-ent)
* [Entity.IsAbility](https://hake.me/docs/entities/entity#entity-isability-ent)
* [Entity.IsTree](https://hake.me/docs/entities/entity#entity-istree-ent)
* [Entity.IsRune](https://hake.me/docs/entities/entity#entity-isrune-ent)
* [Entity.IsPhysicalItem](https://hake.me/docs/entities/entity#entity-isphysicalitem-ent)
* [Entity.IsAlive](https://hake.me/docs/entities/entity#entity-isalive-ent)
* [Entity.IsDormant](https://hake.me/docs/entities/entity#entity-isdormant-ent)
* [Entity.GetHealth](https://hake.me/docs/entities/entity#entity-gethealth-ent)
* [Entity.GetMaxHealth](https://hake.me/docs/entities/entity#entity-getmaxhealth-ent)
* [Entity.GetTeamNum](https://hake.me/docs/entities/entity#entity-getteamnum-ent)
* [Entity.GetOrigin](https://hake.me/docs/entities/entity#entity-getorigin-ent)
* [Entity.GetAbsOrigin](https://hake.me/docs/entities/entity#entity-getabsorigin-ent)
* [Entity.GetRotation](https://hake.me/docs/entities/entity#entity-getrotation-ent)
* [Entity.GetAbsRotation](https://hake.me/docs/entities/entity#entity-getabsrotation-ent)
* [Entity.GetVelocity](https://hake.me/docs/entities/entity#entity-getvelocity-ent)
* [Entity.GetAngVelocity](https://hake.me/docs/entities/entity#entity-getangvelocity-ent)
* [Entity.IsTurning](https://hake.me/docs/entities/entity#entity-isturning-ent)
* [Entity.GetIndex](https://hake.me/docs/entities/entity#entity-getindex-ent)
* [Entity.RecursiveOwnedByIndex](https://hake.me/docs/entities/entity#entity-recursiveownedbyindex-ent-index)
* [Entity.OwnedByHandle](https://hake.me/docs/entities/entity#entity-ownedbyhandle-ent-handle)
* [Entity.OwnedByIndex](https://hake.me/docs/entities/entity#entity-ownedbyindex-ent-index)
* [Entity.OwnedBy](https://hake.me/docs/entities/entity#entity-ownedby-ent-ent2)
* [Entity.GetOwner](https://hake.me/docs/entities/entity#entity-getowner-ent)
* [Entity.GetClassName](https://hake.me/docs/entities/entity#entity-getclassname-ent)
* [Entity.GetLastMessageTime](https://hake.me/docs/entities/entity#entity-getlastmessagetime-ent)
* [Entity.GetEffects](https://hake.me/docs/entities/entity#entity-geteffects-ent)
* [Entity.GetViewerID](https://hake.me/docs/entities/entity#entity-getviewerid-ent)
* [Entity.GetHeroesInRadius](https://hake.me/docs/entities/entity#entity-getheroesinradius-entity-radius-team-includeillusions)
* [Entity.GetUnitsInRadius](https://hake.me/docs/entities/entity#entity-getunitsinradius-entity-radius-team-includeillusions-realunits)
* [Entity.GetTreesInRadius](https://hake.me/docs/entities/entity#entity-gettreesinradius-entity-radius-isactive)
* [Entity.GetField](https://hake.me/docs/entities/entity#entity-getfield-entity)
* [Entity.GetFields](https://hake.me/docs/entities/entity#entity-getfields-entity)
* [Entity.GetModelName](https://hake.me/docs/entities/entity#entity-getmodel-entity)
* [Entity.SetModel](https://hake.me/docs/entities/entity#entity-setmodel-entity-path)
* [Entity.SetScale](https://hake.me/docs/entities/entity#entity-setscale-entity-scale)
* [Entity.SetColorTint](https://hake.me/docs/entities/entity#entity-setcolortint-entity-r-g-b-a)
* [Entity.StartGlowing](https://hake.me/docs/entities/entity#entity-startglowing-entity-r-g-b-a)
* [Entity.StopGlowing](https://hake.me/docs/entities/entity#entity-stopglowing-entity)

---

## `Entity.IsSameTeam(ent, ent2)`​

### Arguments

* ​`ent`​ - The first entity to get the team of
* ​`ent2`​ - The second entity to compare the team of

### Returns

True if the entities are on the same team.

---

## `Entity.IsEntity(ent)`​

### Arguments

* ​`ent`​ - The potential entity to test.

---

## `Entity.IsNPC(ent)`​

### Arguments

* ​`ent`​ - The entity to test.

### Returns

True if the entity is an NPC type entity.

### Remarks

Hero type entities are also NPC type entities.

---

## `Entity.IsHero(ent)`​

### Arguments

* ​`ent`​ - The entity to test.

### Returns

True if the entity is a hero type entity.

---

## `Entity.IsPlayer(ent)`​

---

## `Entity.IsAbility(ent)`​

---

## `Entity.IsTree(ent)`​

---

## `Entity.IsRune(ent)`​

---

## `Entity.IsPhysicalItem(ent)`​

---

## `Entity.IsAlive(ent)`​

---

## `Entity.IsDormant(ent)`​

### Returns

True if entity is dormant.

### Remarks

*Dormant* means most data for this entity is no longer being sent to the client. This is usually the case when an entity is in the Fog of War, or invisible.

---

## `Entity.GetHealth(ent)`​

### Arguments

* ​`ent`​ - The entity.

### Returns

The entity's health as an integer.

---

## `Entity.GetMaxHealth(ent)`​

### Arguments

* ​`ent`​ - The entity.

### Returns

The entity's max health as an integer.

---

## `Entity.GetTeamNum(ent)`​

### Arguments

* ​`ent`​ - The entity.

### Returns

The entity's team's number.

---

## `Entity.GetOrigin(ent)`​

### Returns

A `Vector`​. Not interpolated.

---

## `Entity.GetAbsOrigin(ent)`​

### Returns

A `Vector`​. Interpolated.

---

## `Entity.GetRotation(ent)`​

### Returns

An `Angle`​. Not interpolated.

---

## `Entity.GetAbsRotation(ent)`​

### Returns

An `Angle`​. Interpolated.

---

## `Entity.GetVelocity(ent)`​

---

## `Entity.GetAngVelocity(ent)`​

---

## `Entity.IsTurning(ent)`​

### Remarks

This method is the same as doing `Entity.GetAngVelocity(ent):Length2d() > 0.1`​ but should be prefered if all you need to know is if an entity is turning.

---

## `Entity.GetIndex(ent)`​

---

## `Entity.RecursiveOwnedByIndex(ent, index)`​

---

## `Entity.OwnedByHandle(ent, handle)`​

---

## `Entity.OwnedByIndex(ent, index)`​

---

## `Entity.OwnedBy(ent, ent2)`​

---

## `Entity.GetOwner(ent)`​

---

## `Entity.GetClassName(ent)`​

---

## `Entity.GetLastMessageTime(ent)`​

---

## `Entity.GetEffects(ent)`​

---

## `Entity.GetViewerID(ent)`​

---

## `Entity.GetHeroesInRadius(entity, radius, team, includeIllusions)`​

### Arguments

* ​`entity`​ - The entity.
* ​`radius`​ - The radius around the entity to search.
* ​`team`​ - The Enum.TeamType to search for.
* ​`includeIllusions`​ - *optional* Wether or not to include illusions in the search. Defaults to false.

### Returns

A table of heroes matching the search parameters.

---

## `Entity.GetUnitsInRadius(entity, radius, team, includeIllusions, realUnits)`​

### Arguments

* ​`entity`​ - The entity.
* ​`radius`​ - The radius around the entity to search.
* ​`team`​ - The Enum.TeamType to search for.
* ​`includeIllusions`​ - *optional* Whether or not to include illusions in the search. Defaults to `false`​.
* ​`realUnits`​ - *optional* Controls whether units are returned where `m_iUnitType == 0`​. Defaults to `false`​

### Returns

A table of units matching the search parameters.

---

## `Entity.GetTreesInRadius(entity, radius, isActive)`​

---

## `Entity.GetFields(entity)`​

### Returns

* A table of all the field names belonging to this `entity`​'s class

---

## `Entity.GetField(entity, name)`​

### Remarks

* Returns an exposed field belonging to this `entity`​
* Type can be many things, `integer`​, `string`​, `number`​, `entity`​, etc...
* If the field is a pointer or a structure, a new table is returned with the following fields:

  * ​`GetClassName()`​

    * Returns the class name associated with the structure/pointer
  * ​`GetFields()`​

    * Same as `Entity.GetFields(ent)`​, returns names of all the fields
  * ​`GetField(name)`​

    * Same as `Entity.GetField(ent, name)`​, only 1 parameter
  * ​`SetField(name, value)`​

    * Same as `Entity.SetField(ent, name, value)`​, only 2 parameters
  * **The returned table should never be stored in a global variable, the game could crash if it is used long-term**
* Not all types are supported yet, this is still a work-in-progress! `nil`​ types usually mean it's not supported (or it's actually `nil`​)
* This API will allow a script author to get fields we've not yet added as a native binding

  * EX: `NPC.GetUnitName(ent)`​ is the same as `Entity.GetField(ent, "m_iszUnitName")`​
* If you find yourself using this often, let us know so we can add it as a native lua binding!

### Examples

#### Dumping fields and checking for differences

```
local FieldTest = {}
local hero_fields = nil

local function log_field(ent, name, prefix)
    Log.Write(prefix .. name .. ": " .. tostring(Entity.GetField(ent, name)))
end

local function is_value_same(a, b)
    if type(a) == "userdata" and type(b) == "userdata" and type(getmetatable(a)) == "table" and type(getmetatable(b)) == "table" then
        if a.GetX ~= nil and b.GetX ~= nil then
            return a:GetX() == b:GetX() and a:GetY() == b:GetY() and a:GetZ() == b:GetZ()
        elseif a.GetPitch ~= nil and b.GetPitch ~= nil then
            return a:GetPitch() == b:GetPitch() and a:GetYaw() == b:GetYaw() and a:GetRoll() == b:GetRoll()
        end
    end

    return a == b
end

function FieldTest.OnUpdate()
    local my_hero = Heroes.GetLocal()
    local fields = Entity.GetFields(my_hero)
    local is_first_time = hero_fields == nil

    if is_first_time == true then
        hero_fields = {}
    end

    -- Logs the initial values of the fields, then logs any values that change
    for i, field in ipairs(fields) do
        local value = Entity.GetField(my_hero, field)

        if is_first_time == true or is_value_same(value, hero_fields[field]) == false then
            hero_fields[field] = value
            log_field(my_hero, field, Entity.GetClassName(my_hero) .. ": ")
        end
    end
end

return FieldTest
```

#### Output

```
C_DOTA_Unit_Hero_Pudge: m_iszPrivateVScripts: nil
C_DOTA_Unit_Hero_Pudge: m_pEntity: nil
C_DOTA_Unit_Hero_Pudge: m_worldGroupId: nil
C_DOTA_Unit_Hero_Pudge: m_CScriptComponent: nil
C_DOTA_Unit_Hero_Pudge: m_viewtarget: Vector(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_flexWeight: nil
C_DOTA_Unit_Hero_Pudge: m_blinktoggle: false
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: -1
C_DOTA_Unit_Hero_Pudge: m_CachedViewTarget: Vector(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_iBlink: 0
C_DOTA_Unit_Hero_Pudge: m_iMouthAttachment: 0
C_DOTA_Unit_Hero_Pudge: m_iEyeAttachment: 0
C_DOTA_Unit_Hero_Pudge: m_blinktime: 0.0
C_DOTA_Unit_Hero_Pudge: m_bResetFlexWeightsOnModelChange: true
C_DOTA_Unit_Hero_Pudge: m_prevblinktoggle: false
C_DOTA_Unit_Hero_Pudge: m_iEyeLidUpDownPP: -1
C_DOTA_Unit_Hero_Pudge: m_iEyeLidLeftRightPP: -1
C_DOTA_Unit_Hero_Pudge: m_flMinEyeUpDown: -30.0
C_DOTA_Unit_Hero_Pudge: m_flMaxEyeUpDown: 30.0
C_DOTA_Unit_Hero_Pudge: m_flMinEyeLeftRight: -30.0
C_DOTA_Unit_Hero_Pudge: m_flMaxEyeLeftRight: 30.0
C_DOTA_Unit_Hero_Pudge: m_PhonemeClasses: nil
C_DOTA_Unit_Hero_Pudge: m_CBodyComponent: nil
C_DOTA_Unit_Hero_Pudge: m_NetworkTransmitComponent: nil
C_DOTA_Unit_Hero_Pudge: m_pDummyPhysicsComponent: nil
C_DOTA_Unit_Hero_Pudge: m_nLastThinkTick: 106
C_DOTA_Unit_Hero_Pudge: m_pGameSceneNode: nil
C_DOTA_Unit_Hero_Pudge: m_pCollision: nil
C_DOTA_Unit_Hero_Pudge: m_iMaxHealth: 700
C_DOTA_Unit_Hero_Pudge: m_iHealth: 700
C_DOTA_Unit_Hero_Pudge: m_lifeState: 0
C_DOTA_Unit_Hero_Pudge: m_takedamage: nil
C_DOTA_Unit_Hero_Pudge: m_ubInterpolationFrame: 1
C_DOTA_Unit_Hero_Pudge: m_hSceneObjectController: nil
C_DOTA_Unit_Hero_Pudge: m_nNoInterpolationTick: 106
C_DOTA_Unit_Hero_Pudge: m_flProxyRandomValue: 0.85126119852066
C_DOTA_Unit_Hero_Pudge: m_iEFlags: 12877824
C_DOTA_Unit_Hero_Pudge: m_nWaterType: 0
C_DOTA_Unit_Hero_Pudge: m_bInterpolateEvenWithNoModel: false
C_DOTA_Unit_Hero_Pudge: m_bPredictionEligible: false
C_DOTA_Unit_Hero_Pudge: m_vecNetworkOrigin: Vector(-1664.0, -1216.0, 128.0)
C_DOTA_Unit_Hero_Pudge: m_angNetworkAngles: Angle(0.0, 45.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_nSimulationTick: -1
C_DOTA_Unit_Hero_Pudge: m_iCurrentThinkContext: 0
C_DOTA_Unit_Hero_Pudge: m_aThinkFunctions: nil
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 3.5333335399628
C_DOTA_Unit_Hero_Pudge: m_flSimulationTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_nSceneObjectOverrideFlags: 1
C_DOTA_Unit_Hero_Pudge: m_bHasSuccessfullyInterpolated: false
C_DOTA_Unit_Hero_Pudge: m_bHasAddedVarsToInterpolation: true
C_DOTA_Unit_Hero_Pudge: m_bRenderEvenWhenNotSuccessfullyInterpolated: false
C_DOTA_Unit_Hero_Pudge: m_nInterpolationLatchDirtyFlags: nil
C_DOTA_Unit_Hero_Pudge: m_ListEntry: nil
C_DOTA_Unit_Hero_Pudge: m_flCreateTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_flSpeed: 0.0
C_DOTA_Unit_Hero_Pudge: m_EntClientFlags: 0
C_DOTA_Unit_Hero_Pudge: m_bClientSideRagdoll: false
C_DOTA_Unit_Hero_Pudge: m_iTeamNum: 2
C_DOTA_Unit_Hero_Pudge: m_spawnflags: 0
C_DOTA_Unit_Hero_Pudge: m_nNextThinkTick: -1
C_DOTA_Unit_Hero_Pudge: m_fFlags: 0
C_DOTA_Unit_Hero_Pudge: m_vecAbsVelocity: Vector(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_vecVelocity: nil
C_DOTA_Unit_Hero_Pudge: m_vecBaseVelocity: Vector(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_hEffectEntity: nil
C_DOTA_Unit_Hero_Pudge: m_hOwnerEntity: userdata: 0000023C3D21BF50
C_DOTA_Unit_Hero_Pudge: m_MoveCollide: nil
C_DOTA_Unit_Hero_Pudge: m_MoveType: nil
C_DOTA_Unit_Hero_Pudge: m_Gender: nil
C_DOTA_Unit_Hero_Pudge: m_nWaterLevel: 0
C_DOTA_Unit_Hero_Pudge: m_fEffects: 0
C_DOTA_Unit_Hero_Pudge: m_hGroundEntity: nil
C_DOTA_Unit_Hero_Pudge: m_flFriction: 0.0
C_DOTA_Unit_Hero_Pudge: m_flElasticity: 1.0
C_DOTA_Unit_Hero_Pudge: m_bSimulatedEveryTick: true
C_DOTA_Unit_Hero_Pudge: m_bAnimatedEveryTick: false
C_DOTA_Unit_Hero_Pudge: m_nMinCPULevel: 0
C_DOTA_Unit_Hero_Pudge: m_nMaxCPULevel: 0
C_DOTA_Unit_Hero_Pudge: m_nMinGPULevel: 0
C_DOTA_Unit_Hero_Pudge: m_nMaxGPULevel: 0
C_DOTA_Unit_Hero_Pudge: m_flNavIgnoreUntilTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_iTextureFrameIndex: 0
C_DOTA_Unit_Hero_Pudge: m_ShadowBits: nil
C_DOTA_Unit_Hero_Pudge: m_flFirstReceivedTime: 3.5333335399628
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 3.5333335399628
C_DOTA_Unit_Hero_Pudge: m_hThink: 65535
C_DOTA_Unit_Hero_Pudge: m_fBBoxVisFlags: 0
C_DOTA_Unit_Hero_Pudge: m_bIsValidIKAttachment: false
C_DOTA_Unit_Hero_Pudge: m_bPredictable: false
C_DOTA_Unit_Hero_Pudge: m_bRenderWithViewModels: false
C_DOTA_Unit_Hero_Pudge: m_nSplitUserPlayerPredictionSlot: nil
C_DOTA_Unit_Hero_Pudge: m_hOldMoveParent: nil
C_DOTA_Unit_Hero_Pudge: m_Particles: nil
C_DOTA_Unit_Hero_Pudge: m_vecPredictedScriptFloats: nil
C_DOTA_Unit_Hero_Pudge: m_vecPredictedScriptFloatIDs: nil
C_DOTA_Unit_Hero_Pudge: m_nNextScriptVarRecordID: 0
C_DOTA_Unit_Hero_Pudge: m_vecAngVelocity: Angle(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_flGroundChangeTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_flGravity: 0.0
C_DOTA_Unit_Hero_Pudge: m_DataChangeEventRef: 6
C_DOTA_Unit_Hero_Pudge: m_nCreationTick: 106
C_DOTA_Unit_Hero_Pudge: m_bIsDOTANPC: true
C_DOTA_Unit_Hero_Pudge: m_bIsNPC: false
C_DOTA_Unit_Hero_Pudge: m_bAnimTimeChanged: false
C_DOTA_Unit_Hero_Pudge: m_bSimulationTimeChanged: false
C_DOTA_Unit_Hero_Pudge: m_bIsBlurred: false
C_DOTA_Unit_Hero_Pudge: m_flNextAttack: 0.0
C_DOTA_Unit_Hero_Pudge: m_iAmmo: nil
C_DOTA_Unit_Hero_Pudge: m_hMyWeapons: nil
C_DOTA_Unit_Hero_Pudge: m_hActiveWeapon: nil
C_DOTA_Unit_Hero_Pudge: m_hMyWearables: nil
C_DOTA_Unit_Hero_Pudge: m_bloodColor: 0
C_DOTA_Unit_Hero_Pudge: m_leftFootAttachment: 0
C_DOTA_Unit_Hero_Pudge: m_rightFootAttachment: 0
C_DOTA_Unit_Hero_Pudge: m_nWaterWakeMode: nil
C_DOTA_Unit_Hero_Pudge: m_flWaterWorldZ: 0.0
C_DOTA_Unit_Hero_Pudge: m_flWaterNextTraceTime: -1000.0
C_DOTA_Unit_Hero_Pudge: m_flFieldOfView: 0.69999998807907
C_DOTA_Unit_Hero_Pudge: m_footstepTimer: nil
C_DOTA_Unit_Hero_Pudge: m_CRenderComponent: nil
C_DOTA_Unit_Hero_Pudge: m_iViewerID: -1
C_DOTA_Unit_Hero_Pudge: m_iTeamVisibilityBitmask: 0
C_DOTA_Unit_Hero_Pudge: m_nLastAddDecal: 0
C_DOTA_Unit_Hero_Pudge: m_nRenderMode: nil
C_DOTA_Unit_Hero_Pudge: m_bVisibilityDirtyFlag: true
C_DOTA_Unit_Hero_Pudge: m_nRenderFX: nil
C_DOTA_Unit_Hero_Pudge: m_bAllowFadeInView: false
C_DOTA_Unit_Hero_Pudge: m_clrRender: nil
C_DOTA_Unit_Hero_Pudge: m_RenderAttributeIDs: nil
C_DOTA_Unit_Hero_Pudge: m_RenderAttributeValues: nil
C_DOTA_Unit_Hero_Pudge: m_LightGroup: nil
C_DOTA_Unit_Hero_Pudge: m_bRenderToCubemaps: false
C_DOTA_Unit_Hero_Pudge: m_Collision: nil
C_DOTA_Unit_Hero_Pudge: m_Glow: nil
C_DOTA_Unit_Hero_Pudge: m_flGlowBackfaceMult: 1.0
C_DOTA_Unit_Hero_Pudge: m_fadeMinDist: 0.0
C_DOTA_Unit_Hero_Pudge: m_fadeMaxDist: 0.0
C_DOTA_Unit_Hero_Pudge: m_flFadeScale: 1.0
C_DOTA_Unit_Hero_Pudge: m_flShadowStrength: -1.0
C_DOTA_Unit_Hero_Pudge: m_bHadOverrideEnabledBeforeShadowFade: true
C_DOTA_Unit_Hero_Pudge: m_nAddDecal: 0
C_DOTA_Unit_Hero_Pudge: m_vDecalPosition: Vector(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_vDecalForwardAxis: Vector(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_flDecalRadius: 0.0
C_DOTA_Unit_Hero_Pudge: m_vecViewOffset: nil
C_DOTA_Unit_Hero_Pudge: m_pClientAlphaProperty: nil
C_DOTA_Unit_Hero_Pudge: m_ClientOverrideTint: nil
C_DOTA_Unit_Hero_Pudge: m_bUseClientOverrideTint: false
C_DOTA_Unit_Hero_Pudge: m_CHitboxComponent: nil
C_DOTA_Unit_Hero_Pudge: m_vecForce: Vector(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_nForceBone: 0
C_DOTA_Unit_Hero_Pudge: m_bShouldAnimateDuringGameplayPause: false
C_DOTA_Unit_Hero_Pudge: m_bDontSimulateClientAnimGraph: false
C_DOTA_Unit_Hero_Pudge: m_nMuzzleFlashParity: 0
C_DOTA_Unit_Hero_Pudge: m_pClientsideRagdoll: nil
C_DOTA_Unit_Hero_Pudge: m_bInitModelEffects: true
C_DOTA_Unit_Hero_Pudge: m_builtRagdoll: false
C_DOTA_Unit_Hero_Pudge: m_bIsStaticProp: false
C_DOTA_Unit_Hero_Pudge: m_nOldMuzzleFlashParity: 0
C_DOTA_Unit_Hero_Pudge: m_iEjectBrassAttachment: -1
C_DOTA_Unit_Hero_Pudge: m_bSuppressAnimEventSounds: false
C_DOTA_Unit_Hero_Pudge: m_iCurrentXP: 0
C_DOTA_Unit_Hero_Pudge: m_iAbilityPoints: 1
C_DOTA_Unit_Hero_Pudge: m_flRespawnTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_flRespawnTimePenalty: 0.0
C_DOTA_Unit_Hero_Pudge: m_flStrength: 25.0
C_DOTA_Unit_Hero_Pudge: m_flAgility: 14.0
C_DOTA_Unit_Hero_Pudge: m_flIntellect: 14.0
C_DOTA_Unit_Hero_Pudge: m_flStrengthTotal: 25.0
C_DOTA_Unit_Hero_Pudge: m_flAgilityTotal: 14.0
C_DOTA_Unit_Hero_Pudge: m_flIntellectTotal: 14.0
C_DOTA_Unit_Hero_Pudge: m_iRecentDamage: 0
C_DOTA_Unit_Hero_Pudge: m_fPainFactor: 0.0
C_DOTA_Unit_Hero_Pudge: m_fTargetPainFactor: 0.0
C_DOTA_Unit_Hero_Pudge: m_bLifeState: true
C_DOTA_Unit_Hero_Pudge: m_nFXStunIndex: -1
C_DOTA_Unit_Hero_Pudge: m_nFXSilenceIndex: -1
C_DOTA_Unit_Hero_Pudge: m_nFXDeathIndex: -1
C_DOTA_Unit_Hero_Pudge: m_iPlayerID: 0
C_DOTA_Unit_Hero_Pudge: m_hReplicatingOtherHeroModel: nil
C_DOTA_Unit_Hero_Pudge: m_bReincarnating: false
C_DOTA_Unit_Hero_Pudge: m_bCustomKillEffect: false
C_DOTA_Unit_Hero_Pudge: m_flSpawnedAt: 1.3333330154419
C_DOTA_Unit_Hero_Pudge: m_iPrimaryAttribute: 0
C_DOTA_Unit_Hero_Pudge: m_nLastDrawnHealth: 0
C_DOTA_Unit_Hero_Pudge: m_flHurtAmount: 0.0
C_DOTA_Unit_Hero_Pudge: m_flLastHurtTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_flHurtDecayRate: 0.0
C_DOTA_Unit_Hero_Pudge: m_flLastHealTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_flLastTreeShakeTime: -3.4028234663853e+38
C_DOTA_Unit_Hero_Pudge: m_CenterOnHeroCooldownTimer: nil
C_DOTA_Unit_Hero_Pudge: m_CombinedModels: nil
C_DOTA_Unit_Hero_Pudge: m_nCurrentCombinedModelIndex: 0
C_DOTA_Unit_Hero_Pudge: m_nPendingCombinedModelIndex: 0
C_DOTA_Unit_Hero_Pudge: m_iHeroID: 0
C_DOTA_Unit_Hero_Pudge: m_flCheckLegacyItemsAt: 0.0
C_DOTA_Unit_Hero_Pudge: m_bDisplayAdditionalHeroes: false
C_DOTA_Unit_Hero_Pudge: m_CombinedParticleModels: nil
C_DOTA_Unit_Hero_Pudge: m_vecAttachedParticleIndeces: nil
C_DOTA_Unit_Hero_Pudge: m_hPets: nil
C_DOTA_Unit_Hero_Pudge: m_bBuybackDisabled: nil
C_DOTA_Unit_Hero_Pudge: m_bWasFrozen: nil
C_DOTA_Unit_Hero_Pudge: m_bUpdateClientsideWearables: nil
C_DOTA_Unit_Hero_Pudge: m_bForceBuildCombinedModel: nil
C_DOTA_Unit_Hero_Pudge: m_bRecombineForMaterialsOnly: nil
C_DOTA_Unit_Hero_Pudge: m_bBuildingCombinedModel: nil
C_DOTA_Unit_Hero_Pudge: m_bInReloadEvent: nil
C_DOTA_Unit_Hero_Pudge: m_bStoreOldVisibility: nil
C_DOTA_Unit_Hero_Pudge: m_bResetVisibility: nil
C_DOTA_Unit_Hero_Pudge: m_bStoredVisibility: nil
C_DOTA_Unit_Hero_Pudge: m_bIsPhantom: false
C_DOTA_Unit_Hero_Pudge: m_iUnitType: 0
C_DOTA_Unit_Hero_Pudge: m_bSelectionRingVisible: true
C_DOTA_Unit_Hero_Pudge: m_iCurrentLevel: 1
C_DOTA_Unit_Hero_Pudge: m_bIsAncient: false
C_DOTA_Unit_Hero_Pudge: m_bStolenScepter: false
C_DOTA_Unit_Hero_Pudge: m_bIsNeutralUnitType: false
C_DOTA_Unit_Hero_Pudge: m_bSelectOnSpawn: false
C_DOTA_Unit_Hero_Pudge: m_bIgnoreAddSummonedToSelection: false
C_DOTA_Unit_Hero_Pudge: m_bConsideredHero: false
C_DOTA_Unit_Hero_Pudge: m_bUsesConstantGesture: false
C_DOTA_Unit_Hero_Pudge: m_bUseHeroAbilityNumbers: false
C_DOTA_Unit_Hero_Pudge: m_bHasSharedAbilities: false
C_DOTA_Unit_Hero_Pudge: m_bIsSummoned: false
C_DOTA_Unit_Hero_Pudge: m_bCanBeDominated: true
C_DOTA_Unit_Hero_Pudge: m_bHasUpgradeableAbilities: false
C_DOTA_Unit_Hero_Pudge: m_flHealthThinkRegen: -0.000762939453125
C_DOTA_Unit_Hero_Pudge: m_iIsControllableByPlayer64: 1
C_DOTA_Unit_Hero_Pudge: m_nHealthBarOffsetOverride: -1
C_DOTA_Unit_Hero_Pudge: m_bCanRespawn: false
C_DOTA_Unit_Hero_Pudge: m_iAttackRange: 0
C_DOTA_Unit_Hero_Pudge: m_iCombatClass: 0
C_DOTA_Unit_Hero_Pudge: m_iCombatClassAttack: 0
C_DOTA_Unit_Hero_Pudge: m_iCombatClassDefend: 0
C_DOTA_Unit_Hero_Pudge: m_colorGemColor: nil
C_DOTA_Unit_Hero_Pudge: m_bHasColorGem: false
C_DOTA_Unit_Hero_Pudge: m_iMoveSpeed: 280
C_DOTA_Unit_Hero_Pudge: m_flBaseAttackTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_iUnitNameIndex: 15
C_DOTA_Unit_Hero_Pudge: m_iHealthBarOffset: -1
C_DOTA_Unit_Hero_Pudge: m_iHealthBarHighlightColor: nil
C_DOTA_Unit_Hero_Pudge: m_flMana: 242.93772888184
C_DOTA_Unit_Hero_Pudge: m_flMaxMana: 242.93772888184
C_DOTA_Unit_Hero_Pudge: m_flManaThinkRegen: -0.012210845947266
C_DOTA_Unit_Hero_Pudge: m_iBKBChargesUsed: 0
C_DOTA_Unit_Hero_Pudge: m_iBotDebugData: 0
C_DOTA_Unit_Hero_Pudge: m_bIsIllusion: false
C_DOTA_Unit_Hero_Pudge: m_bHasClientSeenIllusionModifier: false
C_DOTA_Unit_Hero_Pudge: m_hAbilities: nil
C_DOTA_Unit_Hero_Pudge: m_flInvisibilityLevel: 0.0
C_DOTA_Unit_Hero_Pudge: m_flHullRadius: 3.0
C_DOTA_Unit_Hero_Pudge: m_flCollisionPadding: 2.0
C_DOTA_Unit_Hero_Pudge: m_flRingRadius: 0.0
C_DOTA_Unit_Hero_Pudge: m_flProjectileCollisionSize: 0.0
C_DOTA_Unit_Hero_Pudge: m_iszUnitName: npc_dota_hero_pudge
C_DOTA_Unit_Hero_Pudge: m_iszParticleFolder: nil
C_DOTA_Unit_Hero_Pudge: m_iszSoundSet: nil
C_DOTA_Unit_Hero_Pudge: m_iszSelectionGroup: nil
C_DOTA_Unit_Hero_Pudge: m_iszVoiceFile: nil
C_DOTA_Unit_Hero_Pudge: m_iszGameSoundsFile: nil
C_DOTA_Unit_Hero_Pudge: m_iszVoiceBackgroundSound: nil
C_DOTA_Unit_Hero_Pudge: m_iszIdleSoundLoop: nil
C_DOTA_Unit_Hero_Pudge: m_szUnitLabel: nil
C_DOTA_Unit_Hero_Pudge: m_nUnitLabelIndex: 0
C_DOTA_Unit_Hero_Pudge: m_strAnimationModifier: nil
C_DOTA_Unit_Hero_Pudge: m_TerrainSpecificFootstepEffect: nil
C_DOTA_Unit_Hero_Pudge: m_bUseCustomTerrainWeatherEffect: false
C_DOTA_Unit_Hero_Pudge: m_bResourcesLoaded: false
C_DOTA_Unit_Hero_Pudge: m_flTauntCooldown: 0.0
C_DOTA_Unit_Hero_Pudge: m_iCurShop: nil
C_DOTA_Unit_Hero_Pudge: m_szCurShopEntName: nil
C_DOTA_Unit_Hero_Pudge: m_iDayTimeVisionRange: 1800
C_DOTA_Unit_Hero_Pudge: m_iNightTimeVisionRange: 800
C_DOTA_Unit_Hero_Pudge: m_iDamageMin: 0
C_DOTA_Unit_Hero_Pudge: m_iDamageMax: 0
C_DOTA_Unit_Hero_Pudge: m_iDamageBonus: 0
C_DOTA_Unit_Hero_Pudge: m_iTaggedAsVisibleByTeam: 0
C_DOTA_Unit_Hero_Pudge: m_ModifierManager: nil
C_DOTA_Unit_Hero_Pudge: m_Inventory: nil
C_DOTA_Unit_Hero_Pudge: m_nUnitState64: 0
C_DOTA_Unit_Hero_Pudge: m_nUnitDebuffState: 0
C_DOTA_Unit_Hero_Pudge: m_bHasInventory: false
C_DOTA_Unit_Hero_Pudge: m_iAcquisitionRange: 0
C_DOTA_Unit_Hero_Pudge: m_FoWViewID: 0
C_DOTA_Unit_Hero_Pudge: m_iPrevHealthPct: 100
C_DOTA_Unit_Hero_Pudge: m_iPrevLifeState: 0
C_DOTA_Unit_Hero_Pudge: m_iPrevTeam: 0
C_DOTA_Unit_Hero_Pudge: m_bPrevProvidesVision: false
C_DOTA_Unit_Hero_Pudge: m_nPrevControllableMask: 0
C_DOTA_Unit_Hero_Pudge: m_TagTime: nil
C_DOTA_Unit_Hero_Pudge: m_ClickedTime: nil
C_DOTA_Unit_Hero_Pudge: m_IdleRunTransitionTimer: nil
C_DOTA_Unit_Hero_Pudge: m_bAnimationTransitionActive: false
C_DOTA_Unit_Hero_Pudge: m_nAnimationTransitionPoseParameters: nil
C_DOTA_Unit_Hero_Pudge: m_flTimeSinceLastAbilityNag: 3.5333335399628
C_DOTA_Unit_Hero_Pudge: m_iAttackCapabilities: 1
C_DOTA_Unit_Hero_Pudge: m_iSpecialAbility: 0
C_DOTA_Unit_Hero_Pudge: m_iMoveCapabilities: 0
C_DOTA_Unit_Hero_Pudge: m_nPlayerOwnerID: -1
C_DOTA_Unit_Hero_Pudge: m_iszMinimapIcon: nil
C_DOTA_Unit_Hero_Pudge: m_flMinimapIconSize: 0.0
C_DOTA_Unit_Hero_Pudge: m_bMinimapDisableTint: false
C_DOTA_Unit_Hero_Pudge: m_bMinimapDisableRotation: false
C_DOTA_Unit_Hero_Pudge: m_colorHeroGlow: nil
C_DOTA_Unit_Hero_Pudge: m_iNearShopMask: 0
C_DOTA_Unit_Hero_Pudge: m_nPoseParameterTurn: 0
C_DOTA_Unit_Hero_Pudge: m_flLean: 0.0
C_DOTA_Unit_Hero_Pudge: m_anglediff: 0
C_DOTA_Unit_Hero_Pudge: m_bInfoKeyActive: false
C_DOTA_Unit_Hero_Pudge: m_bNewUpdateAssetModifiersNetworked: true
C_DOTA_Unit_Hero_Pudge: m_bSuppressGlow: false
C_DOTA_Unit_Hero_Pudge: m_bWasSinking: false
C_DOTA_Unit_Hero_Pudge: m_flRangeDisplayDist: 0.0
C_DOTA_Unit_Hero_Pudge: m_szDefaultIdle: nil
C_DOTA_Unit_Hero_Pudge: m_damagetimer: nil
C_DOTA_Unit_Hero_Pudge: m_vRenderOrigin: Vector(0.0, 0.0, 0.0)
C_DOTA_Unit_Hero_Pudge: m_fZDelta: 0.0
C_DOTA_Unit_Hero_Pudge: m_flDeathTime: 0.0
C_DOTA_Unit_Hero_Pudge: m_bBaseStatsChanged: true
C_DOTA_Unit_Hero_Pudge: m_bNeedsSoundEmitterRefresh: false
C_DOTA_Unit_Hero_Pudge: m_flPhysicalArmorValue: -2.0
C_DOTA_Unit_Hero_Pudge: m_flMagicalResistanceValue: 25.0
C_DOTA_Unit_Hero_Pudge: m_nPrevSequenceParity: -1
C_DOTA_Unit_Hero_Pudge: m_flPrevInvisLevel: 0.0
C_DOTA_Unit_Hero_Pudge: m_nOriginalModelIndex: nil
C_DOTA_Unit_Hero_Pudge: m_nClientOriginalModelIndex: nil
C_DOTA_Unit_Hero_Pudge: m_iPrevSequence: -1
C_DOTA_Unit_Hero_Pudge: m_pLastWeatherEffectName: nil
C_DOTA_Unit_Hero_Pudge: m_VoiceBackgroundSoundTimer: nil
C_DOTA_Unit_Hero_Pudge: m_bIsWaitingToSpawn: false
C_DOTA_Unit_Hero_Pudge: m_nTotalDamageTaken: 0
C_DOTA_Unit_Hero_Pudge: m_flManaRegen: -0.000762939453125
C_DOTA_Unit_Hero_Pudge: m_flHealthRegen: -0.000762939453125
C_DOTA_Unit_Hero_Pudge: m_bIsMoving: false
C_DOTA_Unit_Hero_Pudge: m_fRevealRadius: 0.0
C_DOTA_Unit_Hero_Pudge: m_hClientOverrideMaterial: nil
C_DOTA_Unit_Hero_Pudge: m_bCombinerMaterialOverrideListChanged: false
C_DOTA_Unit_Hero_Pudge: m_nBaseModelMeshCount: 0
C_DOTA_Unit_Hero_Pudge: m_combinerMaterialOverrideList: nil
C_DOTA_Unit_Hero_Pudge: m_nArcanaLevel: 0
C_DOTA_Unit_Hero_Pudge: m_nDefaultArcanaLevel: 0
C_DOTA_Unit_Hero_Pudge: m_defaultColorGemColor: nil
C_DOTA_Unit_Hero_Pudge: m_bHasBuiltWearableSpawnList: false
C_DOTA_Unit_Hero_Pudge: m_NetworkActivity: 1534
C_DOTA_Unit_Hero_Pudge: m_PrevNetworkActivity: -1
C_DOTA_Unit_Hero_Pudge: m_NetworkSequenceIndex: 1
C_DOTA_Unit_Hero_Pudge: m_bShouldDoFlyHeightVisual: true
C_DOTA_Unit_Hero_Pudge: m_flStartSequenceCycle: 0.0
C_DOTA_Unit_Hero_Pudge: m_ActivityModifiers: nil
C_DOTA_Unit_Hero_Pudge: m_hBackgroundSceneEnt: nil
C_DOTA_Unit_Hero_Pudge: m_hSpeakingSceneEnt: nil
C_DOTA_Unit_Hero_Pudge: m_hOldWearables: nil
C_DOTA_Unit_Hero_Pudge: m_hOldWearableSkins: nil
C_DOTA_Unit_Hero_Pudge: m_CustomHealthLabel: nil
C_DOTA_Unit_Hero_Pudge: m_CustomHealthLabelColor: nil
C_DOTA_Unit_Hero_Pudge: m_nWearableDefIndex: nil
C_DOTA_Unit_Hero_Pudge: m_gibTintColor: nil
C_DOTA_Unit_Hero_Pudge: m_bForceMaterialCombine: false
C_DOTA_Unit_Hero_Pudge: m_bShouldDrawParticlesWhileHidden: false
C_DOTA_Unit_Hero_Pudge: m_bIsClientThinkPending: false
C_DOTA_Unit_Hero_Pudge: m_bActivityModifiersDirty: false
C_DOTA_Unit_Hero_Pudge: m_shadowTimer: nil
C_DOTA_Unit_Hero_Pudge: m_shadowType: nil
C_DOTA_Unit_Hero_Pudge: m_forcedShadowType: nil
C_DOTA_Unit_Hero_Pudge: m_bForceShadowType: true
C_DOTA_Unit_Hero_Pudge: m_bInFrustum: false
C_DOTA_Unit_Hero_Pudge: m_nInFrustumFrame: 0
C_DOTA_Unit_Hero_Pudge: m_flFrustumDistanceSqr: 0.0
C_DOTA_Unit_Hero_Pudge: m_nLod: 0
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: 11
C_DOTA_Unit_Hero_Pudge: m_iEFlags: 12861440
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 3.6333334445953
C_DOTA_Unit_Hero_Pudge: m_hThink: 41
C_DOTA_Unit_Hero_Pudge: m_iViewerID: 5
C_DOTA_Unit_Hero_Pudge: m_bInitModelEffects: false
C_DOTA_Unit_Hero_Pudge: m_nLastDrawnHealth: 700
C_DOTA_Unit_Hero_Pudge: m_iHeroID: 14
C_DOTA_Unit_Hero_Pudge: m_iUnitType: 1
C_DOTA_Unit_Hero_Pudge: m_flHealthThinkRegen: 2.4959716796875
C_DOTA_Unit_Hero_Pudge: m_iAttackRange: 150
C_DOTA_Unit_Hero_Pudge: m_iCombatClassDefend: 1
C_DOTA_Unit_Hero_Pudge: m_flBaseAttackTime: 1.7000000476837
C_DOTA_Unit_Hero_Pudge: m_iHealthBarOffset: 200
C_DOTA_Unit_Hero_Pudge: m_flManaThinkRegen: 0.69279098510742
C_DOTA_Unit_Hero_Pudge: m_flHullRadius: 24.0
C_DOTA_Unit_Hero_Pudge: m_flCollisionPadding: 3.0
C_DOTA_Unit_Hero_Pudge: m_flRingRadius: 70.0
C_DOTA_Unit_Hero_Pudge: m_iszParticleFolder: particles/units/heroes/hero_pudge
C_DOTA_Unit_Hero_Pudge: m_iszSoundSet: Hero_Pudge
C_DOTA_Unit_Hero_Pudge: m_iszVoiceFile: soundevents/voscripts/game_sounds_vo_pudge.vsndevts
C_DOTA_Unit_Hero_Pudge: m_iszGameSoundsFile: soundevents/game_sounds_heroes/game_sounds_pudge.vsndevts
C_DOTA_Unit_Hero_Pudge: m_iszIdleSoundLoop: Hero_Pudge.IdleLoop
C_DOTA_Unit_Hero_Pudge: m_bResourcesLoaded: true
C_DOTA_Unit_Hero_Pudge: m_iDamageMin: 65
C_DOTA_Unit_Hero_Pudge: m_iDamageMax: 71
C_DOTA_Unit_Hero_Pudge: m_iTaggedAsVisibleByTeam: 22
C_DOTA_Unit_Hero_Pudge: m_bHasInventory: true
C_DOTA_Unit_Hero_Pudge: m_iAcquisitionRange: 600
C_DOTA_Unit_Hero_Pudge: m_iPrevTeam: 2
C_DOTA_Unit_Hero_Pudge: m_nPrevControllableMask: 1
C_DOTA_Unit_Hero_Pudge: m_iMoveCapabilities: 1
C_DOTA_Unit_Hero_Pudge: m_bNewUpdateAssetModifiersNetworked: false
C_DOTA_Unit_Hero_Pudge: m_szDefaultIdle: scenes/pudge/pudge_exp_idle_01.vcd
C_DOTA_Unit_Hero_Pudge: m_bNeedsSoundEmitterRefresh: true
C_DOTA_Unit_Hero_Pudge: m_nPrevSequenceParity: 3
C_DOTA_Unit_Hero_Pudge: m_iPrevSequence: 1
C_DOTA_Unit_Hero_Pudge: m_nBaseModelMeshCount: 2
C_DOTA_Unit_Hero_Pudge: m_flStartSequenceCycle: 0.075585871934891
C_DOTA_Unit_Hero_Pudge: m_hBackgroundSceneEnt: userdata: 0000023BF0BD2800
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: 14
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 3.6333334445953
C_DOTA_Unit_Hero_Pudge: m_bHasSuccessfullyInterpolated: true
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 3.6666667461395
C_DOTA_Unit_Hero_Pudge: m_DataChangeEventRef: 2
C_DOTA_Unit_Hero_Pudge: m_iNearShopMask: 7
C_DOTA_Unit_Hero_Pudge: m_bBaseStatsChanged: false
C_DOTA_Unit_Hero_Pudge: m_bNeedsSoundEmitterRefresh: false
C_DOTA_Unit_Hero_Pudge: m_PrevNetworkActivity: 1534
C_DOTA_Unit_Hero_Pudge: m_flStartSequenceCycle: 0.1007811576128
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: 17
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 3.6666667461395
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 3.7000002861023
C_DOTA_Unit_Hero_Pudge: m_flStartSequenceCycle: 0.12597662210464
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: 22
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 3.7000002861023
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 3.7333335876465
C_DOTA_Unit_Hero_Pudge: m_DataChangeEventRef: 3
C_DOTA_Unit_Hero_Pudge: m_flStartSequenceCycle: 0.15117190778255
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: 28
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 3.7333335876465
C_DOTA_Unit_Hero_Pudge: m_iEFlags: 12894208
C_DOTA_Unit_Hero_Pudge: m_vecNetworkOrigin: Vector(-1663.90625, -1206.625, 128.0)
C_DOTA_Unit_Hero_Pudge: m_angNetworkAngles: Angle(0.0, 59.0625, 0.0)
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 5.1666669845581
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 5.2000002861023
C_DOTA_Unit_Hero_Pudge: m_DataChangeEventRef: 3
C_DOTA_Unit_Hero_Pudge: m_anglediff: 29
C_DOTA_Unit_Hero_Pudge: m_NetworkActivity: 1502
C_DOTA_Unit_Hero_Pudge: m_flStartSequenceCycle: 0.0
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: 319
C_DOTA_Unit_Hero_Pudge: m_vecNetworkOrigin: Vector(-1663.78125, -1197.21875, 128.0)
C_DOTA_Unit_Hero_Pudge: m_angNetworkAngles: Angle(0.0, 77.34375, 0.0)
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 5.2000002861023
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 5.2333335876465
C_DOTA_Unit_Hero_Pudge: m_DataChangeEventRef: 2
C_DOTA_Unit_Hero_Pudge: m_flLean: 0.1000000089407
C_DOTA_Unit_Hero_Pudge: m_anglediff: 10
C_DOTA_Unit_Hero_Pudge: m_nPrevSequenceParity: 6
C_DOTA_Unit_Hero_Pudge: m_bIsMoving: true
C_DOTA_Unit_Hero_Pudge: m_PrevNetworkActivity: 1502
C_DOTA_Unit_Hero_Pudge: m_flStartSequenceCycle: 0.029166638851166
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: 325
C_DOTA_Unit_Hero_Pudge: m_vecNetworkOrigin: Vector(-1663.65625, -1187.8125, 128.0)
C_DOTA_Unit_Hero_Pudge: m_angNetworkAngles: Angle(0.0, 80.15625, 0.0)
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 5.2333335876465
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 5.2666668891907
C_DOTA_Unit_Hero_Pudge: m_flLean: 0.082990407943726
C_DOTA_Unit_Hero_Pudge: m_anglediff: 8
C_DOTA_Unit_Hero_Pudge: m_flStartSequenceCycle: 0.058333277702332
C_DOTA_Unit_Hero_Pudge: m_nLastFlexUpdateFrameCount: 331
C_DOTA_Unit_Hero_Pudge: m_vecNetworkOrigin: Vector(-1663.53125, -1178.4375, 128.0)
C_DOTA_Unit_Hero_Pudge: m_angNetworkAngles: Angle(0.0, 88.59375, 0.0)
C_DOTA_Unit_Hero_Pudge: m_flAnimTime: 5.2666668891907
C_DOTA_Unit_Hero_Pudge: m_flLastMessageTime: 5.3000001907349
C_DOTA_Unit_Hero_Pudge: m_flLean: 0.066491067409515
```

---

## `Entity.SetField(entity, name, value)`​

### Sets

A field belonging to this entity to `value`​.

### Remarks

Only supports `number`​ values. **WARNING! This can potentially crash the game or cause instability if some fields are changed**

---

## `Entity.GetModelName(entity)`​

---

## `Entity.SetModel(entity, path)`​

---

## `Entity.SetScale(entity, scale)`​

---

## `Entity.SetColorTint(entity, r, g, b, a)`​

---

## `Entity.StartGlowing(entity, r, g, b, a)`​

---

## `Entity.StopGlowing(entity)`​
