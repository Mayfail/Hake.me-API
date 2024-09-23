# JSON

This table provides functions to encode and decode data in the [JSON](https://www.json.org/) format.

* [JSON.Encode](https://hake.me/docs/systems/json#json-encode-value)
* [JSON.Decode](https://hake.me/docs/systems/json#json-decode-jsonstring)

---

## `JSON.Encode(value)`​

### Arguments

* ​`value`​ - The Lua value to encode

### Returns

A string representing the JSON encoded value.

### Remarks

​`value`​ can be any Lua value except for a userdata, light userdata or function.

---

## `JSON.Decode(jsonString)`​

### Arguments

* ​`jsonString`​ - The JSON string to decode

### Returns

The Lua value representation of the decoded JSON string
