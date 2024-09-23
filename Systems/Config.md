# Config

This table lets your scripts read and write their own config files.

* [Config.ReadFile](https://hake.me/docs/systems/config#config-readefile-filename)
* [Config.WriteFile](https://hake.me/docs/systems/config#config-writefile-filename-data)
* [Config.ReadInt](https://hake.me/docs/systems/config#config-readint-configname-key-defaultvalue)
* [Config.ReadFloat](https://hake.me/docs/systems/config#config-readfloat-configname-key-defaultvalue)
* [Config.ReadString](https://hake.me/docs/systems/config#config-readstring-configname-key-defaultvalue)
* [Config.WriteInt](https://hake.me/docs/systems/config#config-writeint-configname-key-defaultvalue)
* [Config.WriteFloat](https://hake.me/docs/systems/config#config-writefloat-configname-key-defaultvalue)
* [Config.WriteString](https://hake.me/docs/systems/config#config-writestring-configname-key-defaultvalue)

---

## `Config.ReadFile(filename)`​

### Returns

The data contained within `filename`​ as a string.

e.g. `local tbl = JSON.Decode(Config.ReadFile("test.json"))`​

---

## `Config.WriteFile(filename, data)`​

### Arguments

* ​`data`​ - A string

### Remarks

Writes `data`​ to `filename`​ on disk. e.g. `Config.WriteFile("test.json", JSON.Encode(tbl))`​

---

## `Config.ReadInt(configName, key, defaultValue)`​

---

## `Config.ReadFloat(configName, key, defaultValue)`​

---

## `Config.ReadString(configName, key, defaultValue)`​

---

## `Config.WriteInt(configName, key, defaultValue)`​

---

## `Config.WriteFloat(configName, key, defaultValue)`​

---

## `Config.WriteString(configName, key, defaultValue)`​

---
