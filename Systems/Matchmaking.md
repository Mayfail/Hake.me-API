# Matchmaking

This table contains functions for matchmaking.

* [Matchmaking.AcceptMatch](https://hake.me/docs/systems/matchmaking#matchmaking-acceptmatch)
* [Matchmaking.DeclineMatch](https://hake.me/docs/systems/matchmaking#matchmaking-declinematch)
* [Matchmaking.FindMatch](https://hake.me/docs/systems/matchmaking#matchmaking-findmatch-match_type)
* [Matchmaking.StopFindingMatch](https://hake.me/docs/systems/matchmaking#matchmaking-findmatch)
* [Matchmaking.IsFindingMatch](https://hake.me/docs/systems/matchmaking#matchmaking-isfindingmatch)
* [Matchmaking.IsInGame](https://hake.me/docs/systems/matchmaking#matchmaking-isingame)
* [Matchmaking.IsInLobby](https://hake.me/docs/systems/matchmaking#matchmaking-isinlobby)
* [Matchmaking.GetAccountData](https://hake.me/docs/systems/matchmaking#matchmaking-getaccountdata)
* [Matchmaking.GetLobbyData](https://hake.me/docs/systems/matchmaking#matchmaking-getlobbydata)
* [Matchmaking.GetPartyData](https://hake.me/docs/systems/matchmaking#matchmaking-getpartydata)
* [Matchmaking.GetSearchData](https://hake.me/docs/systems/matchmaking#matchmaking-getsearchdata)

---

## `Matchmaking.AcceptMatch()`​

---

## `Matchmaking.DeclineMatch()`​

---

## `Matchmaking.FindMatch(match_type)`​

* ​`match_type`​ - See [Enum.MatchType](https://hake.me/docs/globals/enum#enum-matchtype)
* Starts a match search
* Can be controlled with the following convars:

  * ​`dota_matchgroups_new`​
  * ​`dota_match_game_modes`​
  * ​`dota_match_languages`​
  * ​`dota_match_solo_queue`​

---

## `Matchmaking.StopFindingMatch(accept_cooldown)`​

* ​`accept_cooldown`​- Bool. Defaults to `false`​. Set to `true`​ to accept a matchmaking cooldown at server creation stage.

---

## `Matchmaking.IsFindingMatch()`​

---

## `Matchmaking.IsInGame()`​

---

## `Matchmaking.IsInLobby()`​

---

## `Matchmaking.GetAccountData()`​

### Returns

* The current [CSODOTAGameAccountClient](https://github.com/SteamDatabase/GameTracking-Dota2/blob/master/Protobufs/dota_gcmessages_common.proto#L81) object as a Lua table

---

## `Matchmaking.GetLobbyData()`​

### Returns

* The current [CSODOTALobby](https://github.com/SteamDatabase/GameTracking-Dota2/blob/master/Protobufs/dota_gcmessages_common_match_management.proto#L320) object as a Lua table

---

## `Matchmaking.GetPartyData()`​

### Returns

* The current [CSODOTAParty](https://github.com/SteamDatabase/GameTracking-Dota2/blob/master/Protobufs/dota_gcmessages_common_match_management.proto#L95) object as a Lua table

---

## `Matchmaking.GetSearchData()`​

### Returns

* The current `CMsgStartFindingMatch`​ data

---
