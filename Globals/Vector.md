# Vector

* [Vector](https://hake.me/docs/globals/vector#vector-x-y-z)
* [vec:__tostring](https://hake.me/docs/globals/vector#vec-__tostring)
* [vec:__add](https://hake.me/docs/globals/vector#vec-__add-vec2)
* [vec:__sub](https://hake.me/docs/globals/vector#vec-__sub-vec2)
* [vec:__mul](https://hake.me/docs/globals/vector#vec-__mul-vec2)
* [vec:Get](https://hake.me/docs/globals/vector#vec-get)
* [vec:GetX](https://hake.me/docs/globals/vector#vec-getx)
* [vec:GetY](https://hake.me/docs/globals/vector#vec-gety)
* [vec:GetZ](https://hake.me/docs/globals/vector#vec-getz)
* [vec:Set](https://hake.me/docs/globals/vector#vec-set-x-y-z)
* [vec:SetX](https://hake.me/docs/globals/vector#vec-setx-x)
* [vec:SetY](https://hake.me/docs/globals/vector#vec-setx-y)
* [vec:SetZ](https://hake.me/docs/globals/vector#vec-setx-z)
* [vec:Normalize](https://hake.me/docs/globals/vector#vec-normalize)
* [vec:Normalized](https://hake.me/docs/globals/vector#vec-normalized)
* [vec:Length](https://hake.me/docs/globals/vector#vec-length)
* [vec:LengthSqr](https://hake.me/docs/globals/vector#vec-lengthsqr)
* [vec:Length2D](https://hake.me/docs/globals/vector#vec-length2d)
* [vec:Length2DSqr](https://hake.me/docs/globals/vector#vec-length2dsqr)
* [vec:Dot](https://hake.me/docs/globals/vector#vec-dot-vec2)
* [vec:Dot2D](https://hake.me/docs/globals/vector#vec-dot2d-vec2)
* [vec:Cross](https://hake.me/docs/globals/vector#vec-cross-vec2)
* [vec:Project](https://hake.me/docs/globals/vector#vec-project-vec2)
* [vec:Distance](https://hake.me/docs/globals/vector#vec-distance-vec2)
* [vec:Scale](https://hake.me/docs/globals/vector#vec-scale-scalar)
* [vec:Scaled](https://hake.me/docs/globals/vector#vec-scaled-scalar)
* [vec:ToAngle](https://hake.me/docs/globals/vector#vec-toangle)
* [vec:Rotate](https://hake.me/docs/globals/vector#vec-rotate-angle)
* [vec:Rotated](https://hake.me/docs/globals/vector#vec-rotated-angle)

---

## `Vector(x, y, z)`​

### Arguments

​`x`​, `y`​, and `z`​ are coordinates. All arguments are optional and will default to 0 if not present.

### Returns

A new userdata type representing the vector.

---

## `vec:__tostring()`​

### Returns

A string representation of the Vector.

---

## `vec:__add(vec2)`​

### Arguments

* ​`vec2`​ - the Vector to add.

### Returns

The result of adding `vec2`​ to `vec`​.

---

## `vec:__sub(vec2)`​

### Arguments

* ​`vec2`​ - the vector to subtract.

### Returns

The result of subtracting `vec2`​ from `vec`​.

---

## `vec:__mul(vec2)`​

### Arguments

* ​`vec2`​ - the vector multiply.

### Returns

The result of multiplying `vec`​ by `vec2`​.

---

## `vec:Get()`​

### Returns

The `x`​, `y`​ and `z`​ coordinates of `vec`​.

---

## `vec:GetX()`​

### Returns

The `x`​ coordinate of `vec`​.

---

## `vec:GetY()`​

### Returns

The `y`​ coordinate of `vec`​.

---

## `vec:GetZ()`​

### Returns

The `z`​ coordinate of `vec`​.

---

## `vec:Set(x, y, z)`​

### Arguments

* ​`x`​, `y`​, and `z`​ are the new coordinates to set `vec`​ to.

---

## `vec:SetX(x)`​

### Arguments

* ​`x`​ - The new value of `vec`​'s x coordinate.

---

## `vec:SetY(y)`​

### Arguments

* ​`y`​ - The new value of `vec`​'s y coordinate.

---

## `vec:SetZ(z)`​

### Arguments

* ​`z`​ - The new value of `vec`​'s z coordinate.

---

## `vec:Normalize()`​

### Description

Normalizes `vec`​.

---

## `vec:Normalized()`​

### Returns

A normalized version of `vec`​.

---

## `vec:Length()`​

### Returns

The length of `vec`​ (also known as its magnitude).

---

## `vec:LengthSqr()`​

### Returns

The squared length of `vec`​ which can be useful if comparing magnitudes without incurring the use of a `sqrtf`​ call (eg, is this vec shorter or longer than some other vec).

---

## `vec:Length2D()`​

### Returns

The 2D length of `vec`​ (ignoring the z axis).

---

## `vec:Length2DSqr()`​

### Returns

The squared 2D length of `vec`​ (see `Length2D()`​ and `LengthSqr()`​ above).

---

## `vec:Dot(vec2)`​

### Returns

The dot product of `vec * vec2`​.

---

## `vec:Dot2D(vec2)`​

### Returns

The 2D dot product of `vec * vec2`​ (ignoring the z axis).

---

## `vec:Cross(vec2)`​

### Returns

The cross product of `vec x vec2`​.

---

## `vec:Project(vec2)`​

### Returns

The projected Vector of `vec`​ by `vec2`​.

---

## `vec:Distance(vec2)`​

### Returns

The distance between `vec`​ and `vec2`​.

---

## `vec:Scale(scalar)`​

### Description

Scales `vec`​ by `scalar`​.

---

## `vec:Scaled(scalar)`​

### Returns

A new Vector that is `vec`​ scaled by `scalar`​.

---

## `vec:ToAngle()`​

### Returns

This vector converted to an [angle](https://hake.me/docs/globals/angle).

---

## `vec:Rotate(angle)`​

### Description

Rotates `vec`​ by `angle`​

---

## `vec:Rotated(angle)`​

### Returns

A new Vector that is `vec`​ rotated by `angle`​

---
