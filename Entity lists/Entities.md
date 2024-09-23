# Entities

This table is only available in the **GUI Beta**

This table contains functions that allow you to iterate over all of the entities present in the game.

* [Entities.GetEntityByIndex](https://hake.me/docs/entity-lists/entities#entities-getentitybyindex-index)
* [Entities.GetEntityByHandle](https://hake.me/docs/entity-lists/entities#entities-getentitybyhandle-handle)
* [Entities.Count](https://hake.me/docs/entity-lists/entities#entities-count-class_name)
* [Entities.Get](https://hake.me/docs/entity-lists/entities#entities-get-index-class_name)
* [Entities.GetAll](https://hake.me/docs/entity-lists/entities#entities-getall-class_name)
* [Entities.Contains](https://hake.me/docs/entity-lists/entities#entities-contains-ent)

---

## `Entities.GetEntityByIndex(index)`​

### Returns

An entity using the internal `index`​ used by the game. Index starts at 0.

---

## `Entities.GetEntityByHandle(handle)`​

### Returns

An entity using the internal `handle`​ used by the game.

---

## `Entities.Count(class_name)`​

### Arguments

* ​`class_name`​ - String. Optional. The class name of the entities to count.

  * If this is `nil`​, the entire entity list is counted.

### Returns

An integer representing the number of entities in the game.

### Remarks

Use this to iterate over each entity with `Entities.Get(...)`​.

---

## `Entities.Get(index, class_name)`​

### Arguments

* ​`index`​ - An integer index of the entity to get. Index starts at 1.
* ​`class_name`​ - String. Optional. The class name of the entity to return.

  * If this is `nil`​, it uses the entire entity list.

### Returns

An entity.

---

## `Entities.GetAll(class_name)`​

### Arguments

* ​`class_name`​ - String. Optional. The class name of the entities to return.

  * If this is `nil`​, the entire entity list is returned.

### Returns

A table containing all of the entities relevant to `class_name`​.

---

## `Entities.Contains(ent)`​

### Arguments

* ​`ent`​ - An entity to test.

### Returns

True if the entity exists in the `Entities`​ list, false otherwise.
