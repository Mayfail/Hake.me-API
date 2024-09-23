# MiniMap

This table contains methods letting you add and update icons on the games minimap.

* [MiniMap.Ping](https://hake.me/docs/systems/minimap#minimap-ping-posorunit-type)
* [MiniMap.AddIcon](https://hake.me/docs/systems/minimap#minimap-addicon-index-texture-position-r-g-b-a-timetolive-size)
* [MiniMap.AddIconByName](https://hake.me/docs/systems/minimap#minimap-addiconbyname-index-name-position-r-g-b-a-timetolive-si)
* [MiniMap.DrawLine](https://hake.me/docs/systems/minimap#minimap-drawline-start-end-clientside)
* [MiniMap.StartLine](https://hake.me/docs/systems/minimap#minimap-drawline-vec-clientside)
* [MiniMap.ContinueLine](https://hake.me/docs/systems/minimap#minimap-drawline-vec-clientside)

---

## `MiniMap.Ping(posOrUnit, type)`​

### Arguments

* ​`posOrUnit`​ - The world position to ping or the unit to ping
* ​`type`​ - The ping type (a number from 0-23). A list of ping names can be found in dota vpk `scripts/ping_wheel.txt`​, or check online version [here](https://github.com/SteamDatabase/GameTracking-Dota2/blob/master/game/dota/pak01_dir/scripts/ping_wheel.txt)

### Remarks

We've rate limited this API to every 250ms.

---

## `MiniMap.AddIcon(index, texture, position, r, g, b, a, timeToLive, size)`​

### Arguments

* ​`index`​ - The minimap icon index (can be `nil`​ in which case a new icon is added to the minimap)
* ​`texture`​ - The texture to use for the icon (can be `nil`​ in which case a generic circle texture is used)
* ​`position`​ - The world position
* ​`r`​ - The red color component of the icon
* ​`g`​ - The green color component of the icon
* ​`b`​ - The blue color component of the icon
* ​`a`​ - The alpha component of the icon
* ​`timeToLive`​ - The length in seconds that the icon should live for
* ​`size`​ - The size of the icon on the minimap

### Returns

An index that you can use as the first argument to this function to update the existing minimap icon.

### Remarks

The `texture`​ argument currently must be given from the [Hero.GetIcon](https://hake.me/docs/entities/hero#hero-geticon-hero) function.

---

## `MiniMap.AddIconByName(index, name, position, r, g, b, a, timeToLive, size)`​

### Arguments

* ​`index`​ - The minimap icon index (can be `nil`​ in which case a new icon is added to the minimap)
* ​`name`​ - The name of the texture to use for the icon (can be `nil`​ or empty in which case a generic circle texture is used). A list of texture names can be found in dota vpk `scripts/mod_textures.txt`​, or check online version [here](https://github.com/SteamDatabase/GameTracking-Dota2/blob/master/game/dota/pak01_dir/scripts/mod_textures.txt). Not all of these will work.
* ​`position`​ - The world position
* ​`r`​ - The red color component of the icon
* ​`g`​ - The green color component of the icon
* ​`b`​ - The blue color component of the icon
* ​`a`​ - The alpha component of the icon
* ​`timeToLive`​ - The length in seconds that the icon should live for
* ​`size`​ - The size of the icon on the minimap

### Returns

An index that you can use as the first argument to this function to update the existing minimap icon.

---

## `MiniMap.DrawLine(start, end, clientside)`​

### Arguments

* ​`start`​ - Starting world pos for the line
* ​`end`​ - Ending world pos for the line
* ​`clientside`​ - If true, only draws the line locally, other players can't see it. Defaults to false.

### Remarks

This API is rate limited by the server. Drawing too many lines in too short of a time span will cause the lines to not show up for other players. Because of this, you should queue up lines to be drawn and draw them over a period of time so that your teammates can reliably see them. We may bake this functionality into this API in a future update.

---

## Example usage

```
local t = {}

t.opt = Menu.AddKeyOption({ "TEST", "MiniMap" }, "Add a circle", Enum.ButtonCode.KEY_8)
t.opt2 = Menu.AddKeyOption({ "TEST", "MiniMap" }, "Add specific circle", Enum.ButtonCode.KEY_9)
t.opt3 = Menu.AddKeyOption({ "TEST", "MiniMap" }, "Add hero", Enum.ButtonCode.KEY_0)
t.specificIcon = nil

function t.OnDraw()
    if Menu.IsKeyDownOnce(t.opt) then
        MiniMap.AddIconByName(nil, nil, Input.GetWorldCursorPos(), 255, 0, 255, 255, 3.0, 800)
    end

    if Menu.IsKeyDownOnce(t.opt2) then
        t.specificIcon = MiniMap.AddIconByName(t.specificIcon, nil, Input.GetWorldCursorPos(), 255, 255, 0, 255, 3.0, 800)
    end

    if Menu.IsKeyDownOnce(t.opt3) then
        local me = Heroes.GetLocal()

        if me then
            MiniMap.AddIcon(nil, Hero.GetIcon(me), Input.GetWorldCursorPos(), 255, 255, 255, 128, 3.0, 800)
        end
    end
end

return t
```

---

## `MiniMap.BeginLine(vec, clientside)`​

### Arguments

* ​`start`​ - Starting world pos for the line
* ​`clientside`​ - If true, only draws the line locally, other players can't see it. Defaults to false.

### Remarks

Starts drawing a new line at the point `vec`​ on the minimap

This API is rate limited by the server. Drawing too many lines in too short of a time span will cause the lines to not show up for other players. Because of this, you should queue up lines to be drawn and draw them over a period of time so that your teammates can reliably see them. We may bake this functionality into this API in a future update.

---

## `MiniMap.ContinueLine(vec, clientside)`​

### Arguments

* ​`vec`​ - Starting world pos for the line
* ​`clientside`​ - If true, only draws the line locally, other players can't see it. Defaults to false.

### Remarks

Creates a new line point connecting the previous `BeginLine`​ or `ContinueLine`​.

This API is rate limited by the server. Drawing too many lines in too short of a time span will cause the lines to not show up for other players. Because of this, you should queue up lines to be drawn and draw them over a period of time so that your teammates can reliably see them. We may bake this functionality into this API in a future update.

---
