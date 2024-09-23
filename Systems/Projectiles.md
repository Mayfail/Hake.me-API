# Projectiles

**This table only exists in the GUI Beta!**

---

This table contains functions that can retrieve the state of active projectiles.

* [Projectiles.GetTrackingProjectileByIndex](https://hake.me/docs/systems/projectiles#projectiles-gettrackingprojectilebyindex-index)
* [Projectiles.GetTrackingProjectileByHandle](https://hake.me/docs/systems/projectiles#projectiles-gettrackingprojectilebyhandle-handle)
* [Projectiles.GetLinearProjectileByIndex](https://hake.me/docs/systems/projectiles#projectiles-getlinearprojectilebyindex-index)
* [Projectiles.GetLinearProjectileByHandle](https://hake.me/docs/systems/projectiles#projectiles-getlinearprojectilebyhandle-handle)

---

## `Projectiles.GetTrackingProjectileByIndex(index)`​

### Returns

A tracking projectile with the given raw `index`​. See [Tracking projectile table](https://hake.me/docs/systems/projectiles#tracking-projectile-table)

---

## `Projectiles.GetTrackingProjectileByHandle(handle)`​

### Returns

A tracking projectile with the given `handle`​. See [Tracking projectile table](https://hake.me/docs/systems/projectiles#tracking-projectile-table)

### Remarks

Handles can be retrieved with the `OnProjectile(projectile)`​ callback

---

## `Projectiles.GetLinearProjectileByIndex(index)`​

### Returns

A linear projectile with the given raw `index`​. See [Linear projectile table](https://hake.me/docs/systems/projectiles#linear-projectile-table)

---

## `Projectiles.GetLinearProjectileByHandle(handle)`​

### Returns

A linear projectile with the given `handle`​. See [Linear projectile table](https://hake.me/docs/systems/projectiles#linear-projectile-table)

### Remarks

Handles can be retrieved with the `OnLinearProjectileCreate(projectile)`​ callback

---

## Tracking projectile table:

* ​`handle`​
* ​`speed`​
* ​`position`​

  * Current position
* ​`destination`​

  * Destination position

## Linear projectile table:

* ​`handle`​
* ​`range`​
* ​`start`​

  * Start position
* ​`position`​

  * Current position
* ​`velocity`​

  * Velocity vector

---

## Example script to draw all projectiles:

```
local p = {}

local active_tracking = {}
local active_linear = {}

function p.OnProjectile(projectile)
    active_tracking[projectile.handle] = true
end

function p.OnLinearProjectileCreate(projectile)
    active_linear[projectile.handle] = true
end

function p.OnDraw()
    -- Tracking projectiles
    for handle, _ in pairs(active_tracking) do
        local projectile = Projectiles.GetTrackingProjectileByHandle(handle)

        if projectile ~= nil then
            local x, y, v = Renderer.WorldToScreen(projectile.position)

            Renderer.SetDrawColor(255, 0, 0, 255)
            Renderer.DrawFilledRect(x, y, 10, 10)
        else
            active_tracking[handle] = nil
        end
    end

    -- Linear projectiles
    for handle, _ in pairs(active_linear) do
        local projectile = Projectiles.GetLinearProjectileByHandle(handle)

        if projectile ~= nil then
            local start_x, start_y, start_v = Renderer.WorldToScreen(projectile.start)
            local x, y, v = Renderer.WorldToScreen(projectile.position)

            local end_x, end_y, end_v = Renderer.WorldToScreen(projectile.start + projectile.velocity:Normalized():Scaled(projectile.range))

            if v then
                Renderer.SetDrawColor(255, 0, 0, 255)
                Renderer.DrawFilledRect(x, y, 10, 10)
            end

            if end_v then
                Renderer.SetDrawColor(255, 0, 0, 255)
                Renderer.DrawFilledRect(end_x, end_y, 10, 10)
            end

            if v and start_v and end_v then
                -- start to current pos
                Renderer.SetDrawColor(0, 255, 0, 255)
                Renderer.DrawLine(start_x, start_y, x, y)

                -- current pos to end pos
                Renderer.SetDrawColor(255, 0, 0, 255)
                Renderer.DrawLine(x, y, end_x, end_y)
            end
        else
            active_linear[handle] = nil
        end
    end
end

return p
```
