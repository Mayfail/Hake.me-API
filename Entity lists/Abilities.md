# Abilities

This table contains functions that allow you to iterate over the ability type entities present in the game.

* [Abilities.Count](https://hake.me/docs/entity-lists/abilities#abilities-count)
* [Abilities.Get](https://hake.me/docs/entity-lists/abilities#abilities-get-index)
* [Abilities.GetAll](https://hake.me/docs/entity-lists/abilities#abilities-getall)
* [Abilities.Contains](https://hake.me/docs/entity-lists/abilities#abilities-contains-ent)

---

## `Abilities.Count()`​

### Returns

An integer representing the number of ability type entities in the game.

### Remarks

Use this to iterate over each ability with `Abilities.Get(...)`​.

---

## `Abilities.Get(index)`​

### Arguments

* ​`index`​ - An integer index of the ability type entity to get. Index starts at 1.

### Returns

An ability type entity.

---

## `Abilities.GetAll()`​

### Returns

A table containing all the ability type entities.

### Remarks

This function causes a table allocation and may be slower than using `Abilities.Get()`​.

---

## `Abilities.Contains(ent)`​

### Arguments

* ​`ent`​ - An entity to test.

### Returns

True if the entity exists in the `Abilities`​ list, false otherwise.

### Remarks

This function can be used to determine if an unknown entity is an ability type entity since only ability type entities will be contained in the `Abilities`​ list.
