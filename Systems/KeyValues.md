# KeyValues

This table contains functions to interact with `KeyValues`​ userdata.

* [KeyValues.GetCache](https://hake.me/docs/systems/keyvalues#keyvalues-getcache)
* [KeyValues.FindCachedKV](https://hake.me/docs/systems/keyvalues#keyvalues-findcachedkv-name)
* [KeyValues.MakeTable](https://hake.me/docs/systems/keyvalues#keyvalues-maketable-kv)
* [KeyValues.FindKey](https://hake.me/docs/systems/keyvalues#keyvalues-findkey-kv)
* [KeyValues.GetName](https://hake.me/docs/systems/keyvalues#keyvalues-getname-kv)
* [KeyValues.GetNextKey](https://hake.me/docs/systems/keyvalues#keyvalues-getnextkey-kv)
* [KeyValues.GetFirstSubKey](https://hake.me/docs/systems/keyvalues#keyvalues-getfirstsubkey-kv)
* [KeyValues.GetDataType](https://hake.me/docs/systems/keyvalues#keyvalues-getdatatype-kv)
* [KeyValues.GetString](https://hake.me/docs/systems/keyvalues#keyvalues-getstring-kv)
* [KeyValues.GetFloat](https://hake.me/docs/systems/keyvalues#keyvalues-getfloat-kv)
* [KeyValues.GetInt](https://hake.me/docs/systems/keyvalues#keyvalues-getint-kv)

---

## `KeyValues.GetCache()`​

---

## `KeyValues.FindCachedKV(name)`​

---

## `KeyValues.MakeTable(kv)`​

### Returns

​`kv`​ converted to a Lua table

---

## `KeyValues.FindKey(kv, ...)`​

### Returns

A `KeyValues`​ userdata that can be used with the [KeyValues](https://hake.me/docs/systems/keyvalues) table

### Remarks

* ​`...`​ means variadic arguments (strings)

  * e.g. `KeyValues.FindKey(hero_kv, "ItemSlots", "2", "SlotText")`​

---

## `KeyValues.GetName(kv)`​

### Returns

The name of the key

---

## `KeyValues.GetNextKey(kv)`​

### Returns

A `KeyValues`​ userdata that can be used with the [KeyValues](https://hake.me/docs/systems/keyvalues) table

---

## `KeyValues.GetFirstSubKey(kv)`​

### Returns

A `KeyValues`​ userdata that can be used with the [KeyValues](https://hake.me/docs/systems/keyvalues) table

---

## `KeyValues.GetDataType(kv)`​

### Returns

The data type of the stored value

---

## `KeyValues.GetString(kv)`​

### Returns

The stored value as a string

---

## `KeyValues.GetFloat(kv)`​

### Returns

The stored value as a float

---

## `KeyValues.GetInt(kv)`​

### Returns

The stored value as an integer
