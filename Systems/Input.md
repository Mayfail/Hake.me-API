# Input

* [Input.GetWorldCursorPos](https://hake.me/docs/systems/input#input-getworldcursorpos)
* [Input.GetNearestUnitToCursor](https://hake.me/docs/systems/input#input-getnearestunittocursor-teamnum-teamtype)
* [Input.GetNearestHeroToCursor](https://hake.me/docs/systems/input#input-getnearestherotocursor-teamnum-teamtype)
* [Input.GetNearestTreeToCursor](https://hake.me/docs/systems/input#input-getnearesttreetocursor-active)
* [Input.IsKeyDown](https://hake.me/docs/systems/input#input-iskeydown-key)
* [Input.IsKeyDownOnce](https://hake.me/docs/systems/input#input-iskeydownonce-key)
* [Input.IsInputCaptured](https://hake.me/docs/systems/input#input-isinputcaptured)
* [Input.GetCursorPos](https://hake.me/docs/systems/input#input-getcursorpos)
* [Input.GetScaledCursorPos](https://hake.me/docs/systems/input#input-getscaledcursorpos)
* [Input.IsCursorInRect](https://hake.me/docs/systems/input#input-iscursorinrect-x-y-w-h)
* [Input.IsCursorInBounds](https://hake.me/docs/systems/input#input-iscursorinbounds-x1-y1-x2-y2)

---

## `Input.GetWorldCursorPos()`​

---

## `Input.GetNearestUnitToCursor(teamNum, teamType)`​

---

## `Input.GetNearestHeroToCursor(teamNum, teamType)`​

---

## `Input.GetNearestTreeToCursor(active)`​

---

## `Input.IsKeyDown(key)`​

### Arguments

* ​`key`​ - See [Enum.ButtonCode](https://hake.me/docs/globals/enum#enum-buttoncode)

### Returns

True if the key is down, false otherwise.

### Remarks

This function does **not** take into consideration if the input is being captured (see: [Input.IsInputCaptured()](https://hake.me/docs/systems/input#input-isinputcaptured)).

---

## `Input.IsKeyDownOnce(key)`​

### Arguments

* ​`key`​ - See [Enum.ButtonCode](https://hake.me/docs/globals/enum#enum-buttoncode)

### Returns

True if the key was pressed once, false otherwise.

### Remarks

This function does **not** take into consideration if the input is being captured (see: [Input.IsInputCaptured()](https://hake.me/docs/systems/input#input-isinputcaptured)).

---

## `Input.IsInputCaptured()`​

### Returns

Returns true if keyboard input is being captured (eg. when chatting in the chat box or when typing in the item search box).

---

## `Input.GetCursorPos()`​

---

## `Input.GetScaledCursorPos()`​

### Returns

Returns `Input.GetCursorPos()`​ but scaled to Dota's screen space (510x384).

---

## `Input.IsCursorInRect(x, y, w, h)`​

---

## `Input.IsCursorInBounds(x1, y1, x2, y2)`​
