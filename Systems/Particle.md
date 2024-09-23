# Particle

NOTE: This table is still a work-in-progress and subject to change in the future.

* [Particle.Create](https://hake.me/docs/systems/particle#particle-create-name-attach-entity)
* [Particle.Destroy](https://hake.me/docs/systems/particle#particle-destroy-particle)
* [Particle.SetControlPoint](https://hake.me/docs/systems/particle#particle-setcontrolpoint-particle-point-vec)
* [Particle.SetControlPointOrientation](https://hake.me/docs/systems/particle#particle-setcontrolpointorientation-particle-point-forward-right)

---

## `Particle.Create(name, attach, entity)`​

### Arguments

* ​`name`​ - The name of the particle effect
* ​`attach`​ - The attach type of the particle effect. See [Enum.ParticleAttachment](https://hake.me/docs/globals/enum#enum-particleattachment)
* ​`entity`​ - *optional* The entity the particle is attached to (dependent on the `attach`​ type)

### Returns

The index of the newly created particle effect

---

## `Particle.Destroy(particle)`​

### Arguments

* ​`particle`​ - The particle effect index (returned by `Particle.Create`​) to destroy

### Remarks

You only have to destroy particles that don't end naturally.

---

## `Particle.SetControlPoint(particle, point, vec)`​

### Arguments

* ​`particle`​ - The particle effect index (returned by `Particle.Create`​)
* ​`point`​ - The control point index to set
* ​`vec`​ - The control point value (Vector)

---

## `Particle.SetControlPointOrientation(particle, point, forward, right, up)`​

### Arguments

* ​`particle`​ - The particle effect index (returned by `Particle.Create`​)
* ​`point`​ - The control point index to set the orientation of
* ​`forward`​ - The forward component vector of the orientation
* ​`right`​ - The right component vector of the orientation
* ​`up`​ - The up component vector of the orientation
