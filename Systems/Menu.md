# Menu

This table contains functions that work with menu system allowing you to create and interact with menu options.

* [Menu.AddOption](https://hake.me/docs/systems/menu#menu-addoption-whereat-name-desc-min-max-step-defaultval)
* [Menu.AddImageOption](https://hake.me/docs/systems/menu#menu-addimageoption-whereat-name-desc-image)
* [Menu.AddKeyOption](https://hake.me/docs/systems/menu#menu-addkeyoption-whereat-name-defaultbutton)
* [Menu.PlaceOption](https://hake.me/docs/systems/menu#menu-placeoption-optionid-whereat)
* [Menu.RemoveOption](https://hake.me/docs/systems/menu#menu-removeoption-optionid)
* [Menu.IsEnabled](https://hake.me/docs/systems/menu#menu-isenabled-optionid)
* [Menu.GetValue](https://hake.me/docs/systems/menu#menu-getvalue-optionid)
* [Menu.GetKey](https://hake.me/docs/systems/menu#menu-getkey-optionid)
* [Menu.GetKeys](https://hake.me/docs/systems/menu#menu-getkeys-keyoption)
* [Menu.IsKeyDown](https://hake.me/docs/systems/menu#menu-iskeydown-optionid)
* [Menu.IsKeyDownOnce](https://hake.me/docs/systems/menu#menu-iskeydownonce-optionid)
* [Menu.SetValueName](https://hake.me/docs/systems/menu#menu-setvaluename-optionid-value-name)
* [Menu.SetValue](https://hake.me/docs/systems/menu#menu-setvalue-option-value-triggercallbacks)
* [Menu.GetOption](https://hake.me/docs/systems/menu#menu-getoption-whereat-name)
* [Menu.GetKeyOption](https://hake.me/docs/systems/menu#menu-getkeyoption-whereat-name)
* [Menu.AutoFavorite](https://hake.me/docs/systems/menu#menu-autofavorite-unique_id-panel_id)

---

## `Menu.AddOption(whereAt, name, desc, min, max, step, defaultValue)`​

---

## `Menu.AddImageOption(whereAt, name, desc, image)`​

---

## `Menu.AddKeyOption(whereAt, name, defaultButton)`​

---

## `Menu.PlaceOption(optionID, whereAt)`​

---

## `Menu.RemoveOption(optionID)`​

---

## `Menu.IsEnabled(optionID)`​

---

## `Menu.GetValue(optionID)`​

---

## `Menu.GetKey(optionID)`​

---

## `Menu.GetKeys(keyOption)`​

### Returns

A table of every key in the current keybinding for the option.

---

## `Menu.IsKeyDown(optionID)`​

### Returns

True if the key is down, false otherwise.

### Remarks

This only returns true if the input is not being captured so you do **not** need to explicitly check [Input.IsInputCaptured()](https://hake.me/docs/systems/input#input-isinputcaptured).

---

## `Menu.IsKeyDownOnce(optionID)`​

### Returns

True if the key was pressed once, false otherwise.

### Remarks

This only returns true if the input is not being captured so you do **not** need to explicitly check [Input.IsInputCaptured()](https://hake.me/docs/systems/input#input-isinputcaptured).

---

## `Menu.SetValueName(optionId, value, name)`​

---

## `Menu.SetValue(option, value, triggerCallbacks)`​

### Arguments

* ​`triggerCallbacks`​ - Boolean. Optional.

---

## `Menu.GetOption(whereAt, name)`​

---

## `Menu.GetKeyOption(whereAt, name)`​

---

## `Menu.AutoFavorite(unique_id, panel_id)`​

### Arguments

* ​`unique_id`​ - A unique string identifier for this auto favorite. This let's you easily remove/change what the auto favorite panel is.
* ​`panel_id`​ - Optional. The panel ID as it appears in the config. If omitted, or `nil`​, the existing auto favorite panel corresponding to `unique_id`​ will be removed.

### Example

```
-- Add an auto favorite
Menu.AutoFavorite("my_script_hero", "/My Script/Heroes/Axe")

-- Change an existing auto favorite
Menu.AutoFavorite("my_script_hero", "/My Script/Heroes/IO")

-- Remove an auto favorite.
Menu.AutoFavorite("my_script_hero")
-- Or
Menu.AutoFavorite("my_script_hero", nil)
```
