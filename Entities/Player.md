# Player

This table contains functions that work on player type entities.

* [Player.PrepareUnitOrders](https://hake.me/docs/entities/player#player-prepareunitorders-player-order-target-vector-ability-orde)
* [Player.ExecuteLastOrder](https://hake.me/docs/entities/player#player-executelastorder-player-queue)
* [Player.ExecuteLastOrderByNPC](https://hake.me/docs/entities/player#player-executelastorderbynpc-player-npc-queue)
* [Player.HoldPosition](https://hake.me/docs/entities/player#player-holdposition-player-npc-queue)
* [Player.AttackTarget](https://hake.me/docs/entities/player#player-attacktarget-player-npc-target-queue)
* [Player.GetPlayerID](https://hake.me/docs/entities/player#player-getplayerid-player)
* [Player.GetName](https://hake.me/docs/entities/player#player-getname-player)
* [Player.GetPlayerData](https://hake.me/docs/entities/player#player-getplayerdata-player)
* [Player.GetTeamData](https://hake.me/docs/entities/player#player-getteamdata-player)
* [Player.GetUnreliableGold](https://hake.me/docs/entities/player#player-getunreliablegold-player)
* [Player.GetReliableGold](https://hake.me/docs/entities/player#player-getreliablegold-player)
* [Player.GetTotalEarnedGold](https://hake.me/docs/entities/player#player-gettotalearnedgold-player)
* [Player.GetTotalEarnedXP](https://hake.me/docs/entities/player#player-gettotalearnedxp-player)
* [Player.GetSharedGold](https://hake.me/docs/entities/player#player-getsharedgold-player)
* [Player.GetHeroKillGold](https://hake.me/docs/entities/player#player-getherokillgold-player)
* [Player.GetCreepKillGold](https://hake.me/docs/entities/player#player-getcreepkillgold-player)
* [Player.GetIncomeGold](https://hake.me/docs/entities/player#player-getincomegold-player)
* [Player.GetNetWorth](https://hake.me/docs/entities/player#player-getnetworth-player)
* [Player.GetDenyCount](https://hake.me/docs/entities/player#player-getdenycount-player)
* [Player.GetLastHitCount](https://hake.me/docs/entities/player#player-getlasthitcount-player)
* [Player.GetLastHitMultikill](https://hake.me/docs/entities/player#player-getlasthitmultikill-player)
* [Player.GetNearbyCreepDeathCount](https://hake.me/docs/entities/player#player-getnearbycreepdeathcount-player)
* [Player.GetMissCount](https://hake.me/docs/entities/player#player-getmisscount-player)
* [Player.GetPossibleHeroSelection](https://hake.me/docs/entities/player#player-getpossibleheroselection-player)
* [Player.GetBuybackCooldownTime](https://hake.me/docs/entities/player#player-getbuybackcooldowntime-player)
* [Player.GetBuybackCostTime](https://hake.me/docs/entities/player#player-getbuybackcosttime-player)
* [Player.GetCustomBuybackCooldown](https://hake.me/docs/entities/player#player-getcustombuybackcooldown-player)
* [Player.GetStuns](https://hake.me/docs/entities/player#player-getstuns-player)
* [Player.GetHealing](https://hake.me/docs/entities/player#player-gethealing-player)
* [Player.GetTowerKills](https://hake.me/docs/entities/player#player-gettowerkills-player)
* [Player.GetRoshanKills](https://hake.me/docs/entities/player#player-getroshankills-player)
* [Player.GetObserverWardsPlaced](https://hake.me/docs/entities/player#player-getobserverwardsplaced-player)
* [Player.GetSentryWardsPlaced](https://hake.me/docs/entities/player#player-getsentrywardsplaced-player)
* [Player.GetCreepsStacked](https://hake.me/docs/entities/player#player-getcreepsstacked-player)
* [Player.GetCampsStacked](https://hake.me/docs/entities/player#player-getcampsstacked-player)
* [Player.GetRunePickups](https://hake.me/docs/entities/player#player-getrunepickups-player)
* [Player.GetGoldSpentOnSupport](https://hake.me/docs/entities/player#player-getgoldspentonsupport-player)
* [Player.GetHeroDamage](https://hake.me/docs/entities/player#player-getherodamage-player)
* [Player.GetWardsPurchased](https://hake.me/docs/entities/player#player-getwardspurchased-player)
* [Player.GetWardsDestroyed](https://hake.me/docs/entities/player#player-getwardsdestroyed-player)
* [Player.IsMuted](https://hake.me/docs/entities/player#player-ismuted-player)
* [Player.GetSelectedUnits](https://hake.me/docs/entities/player#player-getselectedunits-player)
* [Player.AddSelectedUnit](https://hake.me/docs/entities/player#player-addselectedunit-player-npc)
* [Player.RemoveSelectedUnit](https://hake.me/docs/entities/player#player-removeselectedunit-player-npc)
* [Player.ClearSelectedUnits](https://hake.me/docs/entities/player#player-clearselectedunits-player)
* [Player.GetAssignedHero](https://hake.me/docs/entities/player#player-getassignedhero-player)
* [Player.GetTeamSlot](https://hake.me/docs/entities/player#player-getteamslot-player)

---

## `Player.PrepareUnitOrders(player, order, target, vector, ability, orderIssuer, npc, queue, showEffects)`​

### Arguments

* ​`player`​ - The player entity.
* ​`order`​ - Order type. See [Enum.UnitOrder](https://hake.me/docs/globals/enum#enum-unitorder)
* ​`target`​ - The target entity. Can be an integer if the order type uses this parameter differently.
* ​`vector`​ - A Vector. Used for orders like `Enum.UnitOrder.DOTA_UNIT_ORDER_MOVE_TO_POSITION`​. Can be 0, 0, 0 if not related to movement orders.
* ​`ability`​ - The ability/item entity to perform an action on. Can be nil if order is not related to abilities. Can be an integer if the order type uses this parameter differently, like buying an item.
* ​`orderIssuer`​ - See [Enum.PlayerOrderIssuer](https://hake.me/docs/globals/enum#enum-playerorderissuer)
* ​`npc`​ - Entity to send these orders to. Usually only relevant if `DOTA_ORDER_ISSUER_PASSED_UNIT_ONLY`​ is passed to orderIssuer. Can be nil otherwise.
* ​`queue`​ - [optional] Boolean. True if this order should be queued. Defaults to false.
* ​`showEffects`​ - [optional] Boolean. True if the effects of this order should be shown.

---

## `Player.ExecuteLastOrder(player, queue)`​

---

## `Player.ExecuteLastOrderByNPC(player, npc, queue)`​

---

## `Player.HoldPosition(player, npc, queue)`​

---

## `Player.AttackTarget(player, npc, target, queue)`​

---

## `Player.GetPlayerID(player)`​

---

## `Player.GetName(player)`​

---

## `Player.GetPlayerData(player)`​

### Returns

A table with the following fields:

* ​`valid`​ - Boolean.
* ​`fullyJoined`​ - Boolean.
* ​`fakeClient`​ - Boolean.
* ​`connectionState`​ - An integer. See [ConnectionState Protobuf enum value](https://github.com/SteamDatabase/Protobufs/blob/master/dota2/dota_shared_enums.proto#L103)
* ​`steamid`​ - SteamID64. To convert into SteamID32(similar to dota friend id), do `SteamID64 & 0xFFFFFFFF`​
* ​`teamNum`​ - An integer. 2 \= Radiant, 3 \= Dire

---

## `Player.GetTeamData(player)`​

### Returns

A table with the following fields:

* ​`kills`​
* ​`assists`​
* ​`deaths`​
* ​`streak`​
* ​`respawnTime`​
* ​`selectedHeroID`​
* ​`teamSlot`​

---

## `Player.GetUnreliableGold(player)`​

---

## `Player.GetReliableGold(player)`​

---

## `Player.GetTotalEarnedGold(player)`​

---

## `Player.GetTotalEarnedXP(player)`​

---

## `Player.GetSharedGold(player)`​

---

## `Player.GetHeroKillGold(player)`​

---

## `Player.GetCreepKillGold(player)`​

---

## `Player.GetIncomeGold(player)`​

---

## `Player.GetNetWorth(player)`​

---

## `Player.GetDenyCount(player)`​

---

## `Player.GetLastHitCount(player)`​

---

## `Player.GetLastHitMultikill(player)`​

---

## `Player.GetNearbyCreepDeathCount(player)`​

---

## `Player.GetMissCount(player)`​

---

## `Player.GetPossibleHeroSelection(player)`​

---

## `Player.GetBuybackCooldownTime(player)`​

---

## `Player.GetBuybackCostTime(player)`​

---

## `Player.GetCustomBuybackCooldown(player)`​

---

## `Player.GetStuns(player)`​

---

## `Player.GetHealing(player)`​

---

## `Player.GetTowerKills(player)`​

---

## `Player.GetRoshanKills(player)`​

---

## `Player.GetObserverWardsPlaced(player)`​

---

## `Player.GetSentryWardsPlaced(player)`​

---

## `Player.GetCreepsStacked(player)`​

---

## `Player.GetCampsStacked(player)`​

---

## `Player.GetRunePickups(player)`​

---

## `Player.GetGoldSpentOnSupport(player)`​

---

## `Player.GetHeroDamage(player)`​

---

## `Player.GetWardsPurchased(player)`​

---

## `Player.GetWardsDestroyed(player)`​

---

## `Player.IsMuted(player)`​

---

## `Player.GetSelectedUnits(player)`​

### Returns

A table containing the units the player has selected (`NPC`​ type entities).

---

## `Player.AddSelectedUnit(player, npc)`​

### Remarks

Adds a single unit to the `player`​'s list of selected units.

---

## `Player.RemoveSelectedUnit(player, npc)`​

### Remarks

Removes a single unit from the `player`​'s list of selected units.

---

## `Player.ClearSelectedUnits(player)`​

### Remarks

Removes all units from the `player`​'s list of selected units.

---

## `Player.GetAssignedHero(player)`​

### Returns

The main hero belonging to this player.

---

## `Player.GetTeamSlot(player)`​

### Returns

The slot that the player occupies on the team (eg, the order in which the player appears in the top bar of the game).
