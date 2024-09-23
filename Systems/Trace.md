# Trace

This table contains functions that let you intract with the games trace system.

* [Trace.FindWorld](https://hake.me/docs/systems/trace#trace-findworld-start-end)
* [Trace.FindEntities](https://hake.me/docs/systems/trace#trace-findentities-start-end-width-height-team-team_type-target_)

---

## `Trace.FindWorld(start, end)`​

### Arguments

* ​`start`​ - The world position ([Vector](https://hake.me/docs/globals/vector)) to begin the trace
* ​`end`​ - The world position ([Vector](https://hake.me/docs/globals/vector)) to end the trace

### Returns

The world position ([Vector](https://hake.me/docs/globals/vector)) of where the intersection with the world occured, or `nil`​ if no intersection with the world occured.

---

## `Trace.FindEntities(start, end, width, height, team, team_type, target_flags, predicate, should_sort)`​

An example script can be found here: [Raycast tester](https://hake.me/docs/introduction/example-scripts#raycast-tester)

### Arguments

* ​`start`​ - The start `Vector`​
* ​`end`​ - The end `Vector`​
* ​`width`​ - Width of the search area between start and end
* ​`height`​ - Height of the search area between start and end
* ​`team`​ - The team number for target\_team
* ​`team_type`​ - See [Enum.TeamType](https://hake.me/docs/globals/enum#enum-teamtype)
* ​`target_flags`​ - See [Enum.TargetType](https://hake.me/docs/globals/enum#enum-targettype)
* ​`predicate`​ - Optional. A boolean function to filter out what is returned e.g. `function(ent) return true end`​
* ​`should_sort`​ - Optional. Bool to sort the result by distance to `start`​. Defaults to `true`​

### Returns

A table of all entities within `start`​, `end`​, `width`​, and `height`​. Can be `nil`​.

### Remarks

This API collides with entities' selection hitbox.

---

## `Trace.FindMouseoverEntity(start, end)`​

### Arguments

* ​`start`​ - Optional, the start position of the ray
* ​`end`​ - Optional, the end position of the ray
* If `start`​ and `end`​ are not set, it uses `Camera.GetOrigin()`​ and `Input.GetWorldCursorPos()`​

### Returns

The first entity hit between start and end.

### Remarks

Uses the same logic as the game's mouseover selection code.
