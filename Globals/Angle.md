# Angle

* [Angle](https://hake.me/docs/globals/angle#angle-pitch-yaw-roll)
* [ang:__tostring](https://hake.me/docs/globals/angle#ang-__tostring)
* [ang:Get](https://hake.me/docs/globals/angle#ang-get)
* [ang:GetPitch](https://hake.me/docs/globals/angle#ang-getpitch)
* [ang:GetYaw](https://hake.me/docs/globals/angle#ang-getyaw)
* [ang:GetRoll](https://hake.me/docs/globals/angle#ang-getroll)
* [ang:Set](https://hake.me/docs/globals/angle#ang-set-pitch-yaw-roll)
* [ang:SetPitch](https://hake.me/docs/globals/angle#ang-setpitch-pitch)
* [ang:SetYaw](https://hake.me/docs/globals/angle#ang-setyaw-yaw)
* [ang:SetRoll](https://hake.me/docs/globals/angle#ang-setroll-roll)
* [ang:GetVectors](https://hake.me/docs/globals/angle#ang-getvectors)
* [ang:GetForward](https://hake.me/docs/globals/angle#ang-getforward)
* [ang:GetRight](https://hake.me/docs/globals/angle#ang-getright)
* [ang:GetUp](https://hake.me/docs/globals/angle#ang-getup)

---

## `Angle(pitch, yaw, roll)`​

### Arguments

​`pitch`​, `yaw`​, and `roll`​ are rotation values. All arguments are optional and will default to 0 if not present.

### Returns

A new userdata type representing the angle.

---

## `ang:__tostring()`​

### Returns

A string representation of the angle.

---

## `ang:Get()`​

### Returns

The `pitch`​, `yaw`​ and `roll`​ rotation values of `ang`​.

---

## `ang:GetPitch()`​

### Returns

The `pitch`​ of `ang`​.

---

## `ang:GetYaw()`​

### Returns

The `yaw`​ of `ang`​.

---

## `ang:GetRoll()`​

### Returns

The `roll`​ of `ang`​.

---

## `ang:Set(pitch, yaw, roll)`​

### Arguments

* ​`pitch`​, `yaw`​, and `roll`​ are the new rotation values to set `ang`​ to.

---

## `ang:SetPitch(pitch)`​

### Arguments

* ​`pitch`​ - The new rotation value of `ang`​'s pitch.

---

## `ang:SetYaw(yaw)`​

### Arguments

* ​`yaw`​ - The new rotation value of `ang`​'s yaw.

---

## `ang:SetRoll(roll)`​

### Arguments

* ​`roll`​ - The new rotation value of `ang`​'s roll.

---

## `ang:GetVectors()`​

### Returns

The forward, right, and up vectors representing this angle.

---

## `ang:GetForward()`​

### Returns

The forward vector of this angle.

---

## `ang:GetRight()`​

### Returns

The right vector of this angle.

---

## `ang:GetUp()`​

### Returns

The up vector of this angle.
