# Wearable

This table is only available in the **GUI Beta**

This table contains functions that work on wearable items (`C_DOTAWearableItem`​)

---

## `Wearable.GetItemDefinition(wearable)`​

### Returns

The item definition table belonging to this wearable

* ​`index`​

  * Index of the item, e.g. 62 is the ID for Juggernaut's legs
* ​`hero_id`​

  * Hero ID associated with the item
* ​`name`​

  * Friendly name of the item
* ​`type`​

  * Type string to be used with Localize.Find
* ​`prefab`​

  * Prefab ("wearable", "default\_item", "bundle", etc...)
* ​`slot_name`​

  * Slot for the item ("head", "arms", "shoulder", etc...)
* ​`image_inventory`​

  * Image path of the item
* ​`player_models`​

  * A table of associated models for this item

---

## `Wearable.GetItemDefinitionIndex(wearable)`​

---

## `Wearable.SetItemDefinitionIndex(wearable, index)`​

### Sets

The item definition index for this wearable item. Changes the model, applies new particle effects, etc...

### Remarks

Item definition indices can be found in `items_game.txt`​ in the game's VPK, or the `ItemSchema`​ API can be used
