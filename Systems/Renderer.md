# Renderer

This table contains functions that work with the rendering system allowing you to draw your own text and shapes. Note that these functions should only be used in the `OnDraw()`​ callback.

* [Renderer.SetDrawColor](https://hake.me/docs/systems/renderer#renderer-setdrawcolor-r-g-b-a)
* [Renderer.DrawLine](https://hake.me/docs/systems/renderer#renderer-drawline-x1-y1-x2-y2)
* [Renderer.DrawFilledRect](https://hake.me/docs/systems/renderer#renderer-drawfilledrect-x-y-w-h)
* [Renderer.DrawOutlineRect](https://hake.me/docs/systems/renderer#renderer-drawoutlinerect-x-y-w-h)
* [Renderer.DrawPixel](https://hake.me/docs/systems/renderer#renderer-drawpixel-x-y)
* [Renderer.LoadFont](https://hake.me/docs/systems/renderer#renderer-loadfont-name-size-weight-italic)
* [Renderer.LoadImage](https://hake.me/docs/systems/renderer#renderer-loadimage-filename)
* [Renderer.DrawText](https://hake.me/docs/systems/renderer#renderer-drawtext-font-x-y-text-shadow)
* [Renderer.DrawImage](https://hake.me/docs/systems/renderer#renderer-drawimage-image-x-y-w-h)
* [Renderer.DrawIcon](https://hake.me/docs/systems/renderer#renderer-drawicon-icon-x-y-w-h)
* [Renderer.DrawTextCenteredX](https://hake.me/docs/systems/renderer#renderer-drawtextcenteredx-font-x-y-text-shadow)
* [Renderer.DrawTextCenteredY](https://hake.me/docs/systems/renderer#renderer-drawtextcenteredy-font-x-y-text-shadow)
* [Renderer.DrawTextCentered](https://hake.me/docs/systems/renderer#renderer-drawtextcentered-font-x-y-text-shadow)
* [Renderer.MeasureText](https://hake.me/docs/systems/renderer#renderer-measuretext-font-text)
* [Renderer.WorldToScreen](https://hake.me/docs/systems/renderer#renderer-worldtoscreen-vec)
* [Renderer.GetScreenSize](https://hake.me/docs/systems/renderer#renderer-getscreensize)
* [Renderer.AddWorldImage](https://hake.me/docs/systems/renderer#renderer-addworldimage-index-image-position-r-g-b-a-timetolive-w)
* [Renderer.AddWorldIcon](https://hake.me/docs/systems/renderer#renderer-addworldicon-index-icon-position-r-g-b-a-timetolive-w-h)

---

## `Renderer.SetDrawColor(r, g, b, a)`​

---

## `Renderer.DrawLine(x1, y1, x2, y2)`​

---

## `Renderer.DrawFilledRect(x, y, w, h)`​

---

## `Renderer.DrawOutlineRect(x, y, w, h)`​

---

## `Renderer.DrawPixel(x, y)`​

---

## `Renderer.LoadFont(name, size, weight, italic, outline_width)`​

---

## `Renderer.LoadImage(fileName)`​

### Remarks

* Loads an image file for later use.
* Supports:

  * ​`vtex_c`​ - compiled texture format for Source 2
  * ​`PNG`​
  * ​`GIF`​
  * ​`ICO`​
  * ​`JPEG`​
  * ​`TIFF`​
* Images can be loaded from the hake.me client directory with:

  * ​`Renderer.LoadImage("~/image.png")`​.
  * ​`"~/"`​ returns a path to `"hake client directory/images/"`​.
* Images can be loaded from the Dota 2 VPK with the direct path to the image, like:

  * ​`Renderer.LoadImage("panorama/images/spellicons/invoker_sun_strike.vtex_c")`​
* To draw the image at normal color, use:

  * ​`Renderer.SetDrawColor(255, 255, 255, 255)`​
* Use a program like GCFScape to figure out where the file paths are.

### Returns

An image handle.

---

## `Renderer.DrawText(font, x, y, text, shadow)`​

---

## `Renderer.DrawImage(image, x, y, w, h)`​

### Arguments

* ​`image`​ - Can either be the image handle returned from `Renderer.LoadImage`​ or a string for the image file path
* ​`x, y`​ - The position to draw the image at
* ​`w, h`​ - Optional. The size to draw the image

### Remarks

Call `Renderer.SetDrawColor`​ before calling this. `Renderer.SetDrawColor(255, 255, 255, 255)`​ will draw the image in its original state. Pre-loading images with `Renderer.LoadImage`​ is technically faster than drawing images with just the string of the image path since it saves on a cache lookup. In practice it will probably not be noticeable at all.

---

## `Renderer.DrawIcon(icon, x, y, w, h)`​

### Arguments

* ​`icon`​ - Optional. Can either be icon returned by `Hero.GetIcon`​ or a string for the icon name
* ​`x, y`​ - The position to draw the icon at
* ​`w, h`​ - Optional. The size to draw the icon

### Remarks

Call `Renderer.SetDrawColor`​ before calling this. `Renderer.SetDrawColor(255, 255, 255, 255)`​ will draw the icon in its original state.

---

## `Renderer.DrawTextCenteredX(font, x, y, text, shadow)`​

---

## `Renderer.DrawTextCenteredY(font, x, y, text, shadow)`​

---

## `Renderer.DrawTextCentered(font, x, y, text, shadow)`​

---

## `Renderer.MeasureText(font, text)`​

### Returns

The width and height of the text if it were drawn.

---

## `Renderer.WorldToScreen(vec)`​

---

## `Renderer.GetScreenSize()`​

---

## `Renderer.AddWorldImage(index, image, position, r, g, b, a, timeToLive, w, h)`​

### Arguments

* ​`index`​ - Optional. The index of the world image to update
* ​`image`​ - The image to use for the world image. Can be an image returned from Renderer.LoadImage or a string with the image path
* ​`position`​ - World space vector to draw the image at
* ​`r, g, b, a`​ - The color to use for the image
* ​`timeToLive`​ - How long the world image should exist for
* ​`w, h`​ - Optional. The size of the drawn world image

### Returns

An index that can be used as the first parameter to update an existing world image.

### Remarks

Draws at full FPS.

---

## `Renderer.AddWorldIcon(index, icon, position, r, g, b, a, timeToLive, w, h)`​

### Arguments

* ​`index`​ - Optional. The index of the world icon to update
* ​`icon`​ - Optional. The icon to use for the world icon. Can be an icon returned from Hero.GetIcon or a string with the icon name
* ​`position`​ - World space vector to draw the icon at
* ​`r, g, b, a`​ - The color to use for the icon
* ​`timeToLive`​ - How long the world icon should exist for
* ​`w, h`​ - Optional. The size of the drawn world icon

### Returns

An index that can be used as the first parameter to update an existing world icon.

### Remarks

Draws at full FPS
