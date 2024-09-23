# Humanizer

This table contains functions that let you interact or control the Humanizer system.

* [Humanizer.MoveCursorTo](https://hake.me/docs/systems/humanizer#humanizer-movecursorto-pos)
* [Humanizer.IsWithinCameraArea](https://hake.me/docs/systems/humanizer#humanizer-iswithincameraarea-vec)

---

## `Humanizer.IsEnabled()`​

---

## `Humanizer.IsInstantMouseMoveEnabled()`​

---

## `Humanizer.IsDiscardOutOfBoundsEnabled()`​

---

## `Humanizer.GetEstimatedDelay(pos)`​

### Arguments

* ​`pos`​ - The world position ([Vector](https://hake.me/docs/globals/vector)) to evaluate.

### Returns

The estimated time (in MS) that an order issued at `pos`​ would take

### Remarks

Does not account for random time settings.

---

## `Humanizer.MoveCursorTo(pos)`​

### Arguments

* ​`pos`​ - The world position ([Vector](https://hake.me/docs/globals/vector)) to move the cursor to

### Remarks

This function only works when the Humanizer is enabled (it's ignored when disabled).

---

## `Humanizer.IsWithinCameraArea(vec)`​

### Arguments

* ​`vec`​ - The world position ([Vector](https://hake.me/docs/globals/vector)) to check if its within the humanized camera's view.

### Returns

​`true`​ if the `vec`​ is within the humanized camera's view, `false`​ otherwise.
