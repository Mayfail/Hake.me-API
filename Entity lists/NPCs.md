# NPCs

This table contains functions that allow you to iterate over the NPC type entities present in the game.

* [NPCs.Count](https://hake.me/docs/entity-lists/npcs#npcs-count)
* [NPCs.Get](https://hake.me/docs/entity-lists/npcs#npcs-get-index)
* [NPCs.GetAll](https://hake.me/docs/entity-lists/npcs#npcs-getall)
* [NPCs.InRadius](https://hake.me/docs/entity-lists/npcs#npcs-inradius-vec-radius-teamnum-teamtype-realunits-illusions)
* [NPCs.Contains](https://hake.me/docs/entity-lists/npcs#npcs-contains-ent)

---

## `NPCs.Count()`​

### Returns

An integer representing the number of NPC type entities in the game.

### Remarks

Use this to iterate over each NPC with `NPCs.Get(...)`​.

---

## `NPCs.Get(index)`​

### Arguments

* ​`index`​ - An integer index of the NPC type entity to get. Index starts at 1.

### Returns

A NPC type entity.

---

## `NPCs.GetAll()`​

### Returns

A table containing all the NPC type entities.

### Remarks

This function causes a table allocation and may be slower than using `NPCs.Get()`​.

---

## `NPCs.InRadius(vec, radius, teamNum, teamType, realUnits, illusions)`​

### Arguments

* ​`vec`​ - The Vector that the search starts from.
* ​`radius`​ - The radius around `vec`​ to search.
* ​`teamNum`​
* ​`teamType`​ - See [Enum.TeamType](https://hake.me/docs/globals/enum#enum-teamtype)
* ​`realUnits`​ - *optional* Controls whether units are returned where `m_iUnitType == 0`​. Defaults to `false`​.
* ​`illusion`​ - *optional* Controls whether units are returned where `NPC.IsIllusion(unit) == true`​. Defaults to `false`​.

### Returns

A table containing the NPCs within the `radius`​ of `vec`​.

---

## `NPCs.Contains(ent)`​

### Arguments

* ​`ent`​ - An entity to test.
* ### Returns

  True if the entity exists in the `NPCs`​ list, false otherwise.

### Remarks

This function can be used to determine if an unknown entity is a NPC type entity since only NPC type entities will be contained in the `NPCs`​ list.
