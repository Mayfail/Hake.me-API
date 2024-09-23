# Runes

This table contains functions that allow you to iterate over the rune type entities present in the game.

* [Runes.Count](https://hake.me/docs/entity-lists/runes#runes-count)
* [Runes.Get](https://hake.me/docs/entity-lists/runes#runes-get-index)
* [Runes.GetAll](https://hake.me/docs/entity-lists/runes#runes-getall)
* [Runes.Contains](https://hake.me/docs/entity-lists/runes#runes-contains-ent)

---

## `Runes.Count()`​

### Returns

An integer representing the number of rune type entities in the game.

### Remarks

Use this to iterate over each rune with `Runes.Get(...)`​.

---

## `Runes.Get(index)`​

### Arguments

* ​`index`​ - An integer index of the rune type entity to get.

### Returns

An rune type entity.

---

## `Runes.GetAll()`​

### Returns

A table containing all the rune type entities.

### Remarks

This function causes a table allocation and may be slower than using `Runes.Get()`​.

---

## `Runes.Contains(ent)`​

### Arguments

* ​`ent`​ - An entity to test.

### Returns

True if the entity exists in the `Runes`​ list, false otherwise.

### Remarks

This function can be used to determine if an unknown entity is an rune type entity since only rune type entities will be contained in the `Runes`​ list.
