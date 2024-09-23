# UI

This table contains functions that allow you to create an Immediate Mode style GUI. All functions only operate when used in the `OnUI`​ callback.

* [UI.BeginWindow](https://hake.me/docs/systems/ui#ui-beginwindow-title-flags)
* [UI.EndWindow](https://hake.me/docs/systems/ui#ui-endwindow)
* [UI.SameLine](https://hake.me/docs/systems/ui#ui-sameline)
* [UI.BeginWrapping](https://hake.me/docs/systems/ui#ui-beginwrapping-flags)
* [UI.EndWrapping](https://hake.me/docs/systems/ui#ui-endwrapping)
* [UI.Indent](https://hake.me/docs/systems/ui#ui-indent)
* [UI.Dedent](https://hake.me/docs/systems/ui#ui-dedent)
* [UI.ClearIndentation](https://hake.me/docs/systems/ui#ui-clearindentation)
* [UI.SetNextID](https://hake.me/docs/systems/ui#ui-setnextid-id)
* [UI.IsItemHovered](https://hake.me/docs/systems/ui#ui-isitemhovered)
* [UI.IsItemActive](https://hake.me/docs/systems/ui#ui-isitemactive)
* [UI.SetNextWindowPos](https://hake.me/docs/systems/ui#ui-setnextwindowpos-x-y-always)
* [UI.SetNextWindowSize](https://hake.me/docs/systems/ui#ui-setnextwindowsize-w-h-always)

Widgets

* [UI.Label](https://hake.me/docs/systems/ui#ui-label-label)
* [UI.WrappedLabel](https://hake.me/docs/systems/ui#ui-wrappedlabel-label)
* [UI.Button](https://hake.me/docs/systems/ui#ui-button-label-stretch)
* [UI.ToggleButton](https://hake.me/docs/systems/ui#ui-togglebutton-label-val)
* [UI.Checkbox](https://hake.me/docs/systems/ui#ui-checkbox-label-val)
* [UI.Tooltip](https://hake.me/docs/systems/ui#ui-tooltip-text)
* [UI.BeginTooltip](https://hake.me/docs/systems/ui#ui-begintooltip-label)
* [UI.EndTooltip](https://hake.me/docs/systems/ui#ui-endtooltip-label)
* [UI.Textbox](https://hake.me/docs/systems/ui#ui-textbox-label-text-placeholder-flags)
* [UI.Dropdown](https://hake.me/docs/systems/ui#ui-dropdown-label-selected-items)
* [UI.Listbox](https://hake.me/docs/systems/ui#ui-listbox-label-selected-items)
* [UI.SliderFloat](https://hake.me/docs/systems/ui#ui-sliderfloat-label-value-min-max)
* [UI.SliderInt](https://hake.me/docs/systems/ui#ui-sliderint-label-value-min-max)
* [UI.TreePush](https://hake.me/docs/systems/ui#ui-treepush-label-flags)
* [UI.TreePop](https://hake.me/docs/systems/ui#ui-treepop)
* [UI.Spacer](https://hake.me/docs/systems/ui#ui-spacer-w-h)
* [UI.BeginMenu](https://hake.me/docs/systems/ui#ui-beginmenu-flags)
* [UI.EndMenu](https://hake.me/docs/systems/ui#ui-endmenu)
* [UI.CloseMenu](https://hake.me/docs/systems/ui#ui-closemenu)
* [UI.Image](https://hake.me/docs/systems/ui#ui-image-img-w-h)
* [UI.ImageButton](https://hake.me/docs/systems/ui#ui-imagebutton-img-w-h)
* [UI.ToggleImage](https://hake.me/docs/systems/ui#ui-toggleimage-img-val-w-h)
* [UI.HR](https://hake.me/docs/systems/ui#ui-hr)

[Examples](https://hake.me/docs/systems/ui#examples)

---

## `UI.BeginWindow(title, flags)`​

### Arguments

* ​`title`​ - The name of the window. Will be used to generate a unique window ID if one hasn't been previously set.
* ​`flags`​ - Bitwise combination of:

  * ​`UI.WindowFlag.HAS_TITLEBAR`​
  * ​`UI.WindowFlag.IS_CLOSABLE`​
  * ​`UI.WindowFlag.IS_DRAGGABLE`​
  * ​`UI.WindowFlag.IS_SCROLLABLE`​
  * ​`UI.WindowFlag.IS_CONTAINED_WITHIN_PARENT`​
  * ​`UI.WindowFlag.STANDARD`​

### Returns

True if the window is open. False if the window should be closed (user has pressed the close button for instance). Make sure you call `UI.EndWindow`​ when this function returns true.

---

## `UI.EndWindow()`​

### Remarks

Ends the current window (the window that has most recently been started using `UI.BeginWindow`​).

---

## `UI.SameLine()`​

### Remarks

Causes the next widget to appear on the same vertical level as the previous widget.

---

## `UI.BeginWrapping(flags)`​

### Arguments

* ​`flags`​ - Optional. Either `UI.WrappingFlag.WINDOW`​ (default) or `UI.WrappingFlag.ITEM`​

### Remarks

Sets the current windows wrapping mode. Essentially this sets a maximum width the current line can get to before `UI.SameLine`​ is ignored.

---

## `UI.EndWrapping()`​

### Remarks

Clears the current wrapping mode.

---

## `UI.Indent()`​

### Remarks

Causes the next widget(s) to appear indentent (further horizontally).

---

## `UI.Dedent()`​

### Remarks

Undoes a single `UI.Indent()`​ call for the next widget(s).

---

## `UI.ClearIndentation()`​

### Remarks

Undoes all `UI.Indent()`​ calls for the next widget(s).

---

## `UI.SetNextID(id)`​

### Arguments

* ​`id`​ - A string or number uniquely identifying the next widget

### Remarks

Widgets are automatically assigned an ID based on their label usually. Sometimes you want to reuse the same label for multiple widgets which can cause problems such as the incorrect widget being interacted with. To fix this interaction you can use `UI.SetNextID(...)`​ to ensure each interactable widget recieves its own unique ID.

---

## `UI.IsItemHovered()`​

### Returns

​`true`​ when the previous widget is currently hovered by the mouse.

---

## `UI.IsItemActive()`​

### Returns

​`true`​ when the previous interactable widget was the last widget activated by the mouse (clicked on).

---

## `UI.SetNextWindowPos(x, y, always)`​

### Arguments

* ​`x`​ - The x pos of the next window
* ​`y`​ - The y pos of the next window
* ​`always`​ - An optional `bool`​ to determine if the next window's pos should always be set every frame (making the window unmovable by the user). If this is false the windows pos is only set once when it is first created.

---

## `UI.SetNextWindowSize(w, h, always)`​

### Arguments

* ​`w`​ - The width of the next window
* ​`h`​ - The height of the next window
* ​`always`​ - An optional `bool`​ to determine if the next window's size should always be set every frame (making the window unresizable by the user). If this is false the windows size is only set once when it is first created.

---

## `UI.Label(label)`​

### Remarks

An uninteractable widget that just displays the `label`​.

---

## `UI.WrappedLabel(label)`​

### Remarks

A label that respects the current wrapping mode (set by `UI.BeginWrapping`​). Newlines will automatically be inserted to wrap the text at the appropriate width.

---

## `UI.Button(label, stretch)`​

### Arguments

* ​`stretch`​ - Optional `bool`​. Will stretch the button horizontally when true.

### Returns

​`true`​ when the button has been clicked.

---

## `UI.ToggleButton(label, val)`​

### Arguments

* ​`val`​ - `bool`​ representing the state of the widget

### Returns

A tuple of `result`​ and `val`​ where `result`​ is true when the widget has been clicked, and `val`​ is the new state of the widget.

---

## `UI.Checkbox(label, val)`​

### Arguments

* ​`val`​ - `bool`​ representing the state of the widget

### Returns

A tuple of `result`​ and `val`​ where `result`​ is true when the widget has been clicked, and `val`​ is the new state of the widget.

---

## `UI.Tooltip(text)`​

### Remarks

Creates a tooltip when the previous widget is hovered that displays `text`​.

---

## `UI.BeginTooltip(label)`​

### Returns

​`true`​ when the previous widget is hovered. Make sure to call `UI.EndTooltip`​ when `UI.BeginTooltip`​ returns `true`​.

---

## `UI.EndTooltip(label)`​

### Remarks

Ends the previously started tooltip.

---

## `UI.Textbox(label, text, placeholder, flags)`​

### Arguments

* ​`text`​ - The text displayed in the textbox
* ​`placeholder`​ - The text displayed in the textbox when `text`​ argument is empty
* ​`flags`​ - Bitwise combination of:

  * ​`UI.TextboxFlag.PASSWORD`​
  * ​`UI.TextboxFlag.READONLY`​
  * ​`UI.TextboxFlag.HAS_CLEAR_BUTTON`​

### Returns

A tuple of `result`​ and `text`​ where `result`​ is `true`​ when the text has been changed and `text`​ is the new text that should be displayed.

---

## `UI.Dropdown(label, selected, items)`​

### Arguments

* ​`selected`​ - The index into the `items`​ table of the selected items
* ​`items`​ - A table of items that can be selected

### Returns

A tuple of `result`​ and `selected`​ where `result`​ is `true`​ when the selected item has been changed and `selected`​ is the newly selected index.

---

## `UI.Listbox(label, selected, items)`​

### Arguments

* ​`selected`​ - The index into the `items`​ table of the selected items
* ​`items`​ - A table of items that can be selected

### Returns

A tuple of `result`​ and `selected`​ where `result`​ is `true`​ when the selected item has been changed and `selected`​ is the newly selected index.

---

## `UI.SliderFloat(label, value, min, max)`​

### Arguments

* ​`value`​ - The current value of the slider
* ​`min`​ - The min value of the slider
* ​`max`​ - The max value of the slider

### Returns

A tuple of `result`​ and `value`​ where result is `true`​ when the slider has been moved and `value`​ is the newly selected value.

---

## `UI.SliderInt(label, value, min, max)`​

### Arguments

* ​`value`​ - The current value of the slider
* ​`min`​ - The min value of the slider
* ​`max`​ - The max value of the slider

### Returns

A tuple of `result`​ and `value`​ where result is `true`​ when the slider has been moved and `value`​ is the newly selected value

---

## `UI.TreePush(label, flags)`​

### Arguments

* ​`flags`​ - Bitwise combination of:

  * ​`UI.TreeFlag.OPENED_BY_DEFAULT`​

### Returns

​`true`​ when the tree is open. Make sure to call `UI.PopTree`​ when `UI.PushTree`​ returns `true`​.

---

## `UI.TreePop()`​

### Remarks

Ends the current tree leaf.

---

## `UI.Spacer(w, h)`​

### Arguments

* ​`w`​ - an optional width of the spacer
* ​`h`​ - an optional height of the spacer

### Remarks

It's just a blank uninteractable widget for spacing purposes.

---

## `UI.BeginMenu(flags)`​

### Arguments

* ​`flags`​ - One of:

  * ​`UI.MenuFlag.OPENS_ON_RIGHT_CLICK`​ - this is the default behavior.
  * ​`UI.MenuFlag.OPENS_ON_LEFT_CLICK`​

### Returns

​`true`​ when the menu is open. Make sure to call `UI.EndMenu`​ when `UI.BeginMenu`​ returns `true`​.

### Remarks

A menu is just a window that appears over the previous widget when the previous widget is clicked. Since its an entirely new window you can add whatever widgets/interactions you want to this menu.

---

## `UI.EndMenu()`​

### Remarks

Ends the previously started menu.

---

## `UI.CloseMenu()`​

### Remarks

Closes the currently open menu. You generally don't need to call this on your own since open menus will automatically close when the user interacts with a different window.

---

## `UI.Image(img, w, h)`​

### Arguments

* ​`img`​ - The image to display (either a `string`​ path to an image or an image handle returned by `Renderer.LoadImage`​)
* ​`w`​ - An optional width for the image
* ​`h`​ - An optional height for the image

---

## `UI.ImageButton(img, w, h)`​

### Arguments

* ​`img`​ - The image to display (either a `string`​ path to an image or an image handle returned by `Renderer.LoadImage`​)
* ​`w`​ - An optional width for the image
* ​`h`​ - An optional height for the image

### Returns

​`true`​ when the image button has been pressed.

---

## `UI.ToggleImage(img, val, w, h)`​

### Arguments

* ​`img`​ - The image to display (either a `string`​ path to an image or an image handle returned by `Renderer.LoadImage`​)
* ​`val`​ - The toggle state of the widget
* ​`w`​ - An optional width for the image
* ​`h`​ - An optional height for the image

### Returns

A tuple of `result`​ and `val`​ where `result`​ is `true`​ when the image toggle has been toggled and `val`​ is the new toggle state.

---

## `UI.HR()`​

### Remarks

A horizontal line to sperate logical groups of widgets within the same window.

---

## Examples

Menu option that opens a new window:

```
local open_ui = Menu.AddOption({"Cool Stuff"}, "Open the UI", "Opens the Cool Stuff UI")
return {
    OnUI = function() 
        if Menu.IsEnabled(open_ui) then
            if UI.BeginWindow("Cool Stuff UI") then
                UI.Label("Look at how cool this UI is")
                UI.EndWindow()
            else
                Menu.SetValue(open_ui, 0)
            end
        end
    end
}
```

Simple menu:

```
local ui_options = {
    option_1 = {
        name = "cool option 1",
        desc = "does something rly cool and neat",
        value = false
    },
    option_2 = {
        name = "cool option 2",
        desc = "does something rly neat but also rly cool",
        value = true
    },
    option_3 = {
        name = "cool option 3",
        desc = "wow this options rly nice and very cool",
        value = true
    },
}

return {
    OnUI = function()
        if UI.BeginWindow("My Cool Menu") then
            for k, option in pairs(ui_options) do 
                local changed, value = UI.Checkbox(option.name, option.value)

                if changed then
                    option.value = value
                end

                UI.Tooltip(option.desc)
            end

            UI.EndWindow()
        end
    end
}
```
