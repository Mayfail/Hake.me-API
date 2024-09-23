# Trees

This table contains functions that allow you to iterate over the tree type entities present in the game.

* [Trees.Count](https://hake.me/docs/entity-lists/trees#trees-count)
* [Trees.Get](https://hake.me/docs/entity-lists/trees#trees-get-index)
* [Trees.GetAll](https://hake.me/docs/entity-lists/trees#trees-getall)
* [Trees.InRadius](https://hake.me/docs/entity-lists/trees#trees-inradius-vec-radius-active)
* [Trees.Contains](https://hake.me/docs/entity-lists/trees#trees-contains-ent)

---

## `Trees.Count()`​

### Returns

An integer representing the number of tree type entities in the game.

### Remarks

Use this to iterate over each tree with `Trees.Get(...)`​.

---

## `Trees.Get(index)`​

### Arguments

* ​`index`​ - An integer index of the tree type entity to get. Index starts at 1.

### Returns

An tree type entity.

---

## `Trees.GetAll()`​

### Returns

A table containing all the tree type entities.

### Remarks

This function causes a table allocation and may be slower than using `Trees.Get()`​.

---

## `Trees.InRadius(vec, radius, active)`​

### Arguments

* ​`vec`​ - The Vector that the search starts from.
* ​`radius`​ - The radius around `vec`​ to search.
* ​`active`​ - Boolean. True if only active (not destroyed) should be returned. Defaults to true.

### Returns

A table containing the trees within the `radius`​ of `vec`​.

---

## `Trees.Contains(ent)`​

### Arguments

* ​`ent`​ - An entity to test.

### Returns

True if the entity exists in the `Trees`​ list, false otherwise.

### Remarks

This function can be used to determine if an unknown entity is an tree type entity since only tree type entities will be contained in the `Trees`​ list.
