# Players

This table contains functions that allow you to iterate over the player type entities present in the game.

* [Players.Count](https://hake.me/docs/entity-lists/players#players-count)
* [Players.Get](https://hake.me/docs/entity-lists/players#players-get-index)
* [Players.GetAll](https://hake.me/docs/entity-lists/players#players-getall)
* [Players.Contains](https://hake.me/docs/entity-lists/players#players-contains-ent)
* [Players.GetLocal](https://hake.me/docs/entity-lists/players#players-getlocal)
* [Players.GetByPlayerID](https://hake.me/docs/entity-lists/players#players-getbyplayerid-id)

---

## `Players.Count()`​

### Returns

An integer representing the number of player type entities in the game.

### Remarks

Use this number to iterate over each players with `Players.Get(...)`​.

---

## `Players.Get(index)`​

### Arguments

* ​`index`​ - An integer index of the player type entity to get. Index starts at 1.

### Returns

A player type entity.

---

## `Players.GetAll()`​

### Returns

A table containing all the player type entities.

### Remarks

This function causes a table allocation and may be slower than using `Players.Get()`​.

---

## `Players.Contains(ent)`​

### Arguments

* ​`ent`​ - An entity to test.

### Returns

True if the entity exists in the `Players`​ list, false otherwise.

### Remarks

This function can be used to determine if an unknown entity is a player type entity since only player type entities will be contained in the `Players`​ list.

---

## `Players.GetLocal()`​

### Returns

Returns the local player's player type entity.

---

## `Players.GetByPlayerID(id)`​

### Returns

Returns a player with the corresponding `id`​.
