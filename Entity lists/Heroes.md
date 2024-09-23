# Heroes

This table contains functions that allow you to iterate over the hero type entities present in the game.

* [Heroes.Count](https://hake.me/docs/entity-lists/heroes#heroes-count)
* [Heroes.GetAll](https://hake.me/docs/entity-lists/heroes#heroes-get-index)
* [Heroes.Contains](https://hake.me/docs/entity-lists/heroes#heroes-contains-ent)
* [Heroes.InRadius](https://hake.me/docs/entity-lists/heroes#heroes-inradius-vec-radius-teamnum-teamtype)
* [Heroes.GetLocal](https://hake.me/docs/entity-lists/heroes#heroes-getlocal)

---

## `Heroes.Count()`​

### Returns

An integer representing the number of hero type entities in the game.

### Remarks

Use this number to iterate over each hero with `Heroes.Get(...)`​.

---

## `Heroes.Get(index)`​

### Arguments

* ​`index`​ - An integer index of the hero type entity to get. Index starts at 1.

### Returns

A hero type entity.

---

## `Heroes.GetAll()`​

### Returns

A table containing all the hero type entities.

### Remarks

This function causes a table allocation and may be slower than using `Heroes.Get()`​.

---

## `Heroes.Contains(ent)`​

### Arguments

* ​`ent`​ - An entity to test.

### Returns

True if the entity exists in the `Heroes`​ list, false otherwise.

### Remarks

This function can be used to determine if an unknown entity is a hero type entity since only hero type entities will be contained in the `Heroes`​ list.

---

## `Heroes.InRadius(vec, radius, teamNum, teamType)`​

### Arguments

* ​`vec`​ - The Vector that the search starts from.
* ​`radius`​ - The radius around `vec`​ to search.
* ​`teamNum`​
* ​`teamType`​ - See [Enum.TeamType](https://hake.me/docs/globals/enum#enum-teamtype)

### Returns

A table containing the heroes within the `radius`​ of `vec`​.

---

## `Heroes.GetLocal()`​

### Returns

Returns the local player's hero type entity.
