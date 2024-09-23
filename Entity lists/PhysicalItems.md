# PhysicalItems

This table contains functions that allow you to iterate over the physical item type entities present in the game. A physical item is an item on the ground.

* [PhysicalItems.Count](https://hake.me/docs/entity-lists/physicalitems#physicalitems-count)
* [PhysicalItems.Get](https://hake.me/docs/entity-lists/physicalitems#physicalitems-get-index)
* [PhysicalItems.GetAll](https://hake.me/docs/entity-lists/physicalitems#physicalitems-getall)
* [PhysicalItems.Contains](https://hake.me/docs/entity-lists/physicalitems#physicalitems-contains-ent)

---

## `PhysicalItems.Count()`​

### Returns

An integer representing the number of physical item type entities in the game.

### Remarks

Use this to iterate over each physical item with `PhysicalItems.Get(...)`​.

---

## `PhysicalItems.Get(index)`​

### Arguments

* ​`index`​ - An integer index of the physical item type entity to get. Index starts at 1.

### Returns

An physical item type entity.

---

## `PhysicalItems.GetAll()`​

### Returns

A table containing all the physical item type entities.

### Remarks

This function causes a table allocation and may be slower than using `PhysicalItems.Get()`​.

---

## `PhysicalItems.Contains(ent)`​

### Arguments

* ​`ent`​ - An entity to test.

### Returns

True if the entity exists in the `PhysicalItems`​ list, false otherwise.

### Remarks

This function can be used to determine if an unknown entity is an physical item type entity since only physical item type entities will be contained in the `PhysicalItems`​ list.
