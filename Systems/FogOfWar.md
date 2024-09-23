# FogOfWar

* [FogOfWar.IsPointVisible](https://hake.me/docs/systems/fogofwar#fogofwar-ispointvisible-vec)
* [FogOfWar.GetPointVisibility](https://hake.me/docs/systems/fogofwar#fogofwar-getpointvisibility-vec-radius)

---

## `FogOfWar.IsPointVisible(vec)`​

### Returns

True if the point at `vec`​ is visible to the player.

---

## `FogOfWar.GetPointVisibility(vec, radius)`​

### Arguments

* ​`radius`​ - Defaults to 0.0

### Returns

A number from `[0.0, 1.0]`​ determining how visible the `radius`​ around `vec`​ is.
