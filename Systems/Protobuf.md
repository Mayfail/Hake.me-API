# Protobuf

Table for working with all things related to Protobuf messages

Relevant messages can be found here: [https://github.com/SteamDatabase/GameTracking-Dota2/tree/master/Protobufs](https://github.com/SteamDatabase/GameTracking-Dota2/tree/master/Protobufs)

---

## `Protobuf.Create(name)`​

### Arguments

* ​`name`​ - string

  * Can be a class name, e.g. `"CMsgStopFindingMatch"`​
  * Can be an enum name, e.g. `"k_EMsgGCStopFindingMatch"`​

### Returns

A `protobuf`​ userdata that can be used with `GCClient.SendMessage`​

* ​`protobuf:AsTable()`​

  * Returns the protobuf as a Lua table
* ​`protobuf:SetField(name, value)`​

  * e.g. `CMsgInviteToParty:SetField("steam_id", 12345)`​
  * Also works like: `CMsgInviteToParty["steam_id"] = 12345`​
* ​`protobuf:CopyFromTable(tbl)`​

  * Copies the values from `tbl`​ into the protobuf

---

## `Protobuf.GetTypeFromMsgName(name)`​

### Arguments

* ​`name`​ - string

  * Can be a class name, e.g. `"CMsgStopFindingMatch"`​
  * Can be an enum name, e.g. `"k_EMsgGCStopFindingMatch"`​

### Returns

The type index associated with `name`​

* e.g `Protobuf.GetTypeFromMsgName("k_EMsgGCStartFindingMatch")`​ will return 7033
* ​`Protobuf.GetTypeFromMsgName("CMsgStartFindingMatch")`​ will *also* return 7033

---

## `Protobuf.GetNameFromType(msgtype)`​

### Arguments

* ​`msgtype`​ - integer

### Returns

The enum name associated with `msgtype`​

* e.g. `Protobuf.GetNameFromType(7033)`​ will return `"k_EMsgGCStartFindingMatch"`​
