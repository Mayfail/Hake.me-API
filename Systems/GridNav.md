# GridNav

## `GridNav.GetNode(x, y)`​

* Returns the value of a specific node at the specified `x`​ and `y`​ or `index`​
* Can also be called like `GridNav.GetNode(index)`​
* How to tell if a node is walkable:

  * ​`local walkable = (GridNav.GetNode(index) & 0x103) == 1`​

---

## `GridNav.GetNodeCount()`​

* Returns the number of nodes within the Grid

---

## `GridNav.GetDimensions()`​

* Returns the Width and Height of the Grid
* e.g. `local dims = GridNav.GetDimensions()`​

---

## `GridNav.GetBounds()`​

* Returns a tuple of min `x`​, `y`​ and max `x`​, `y`​ 2D Vectors for the Grid
* e.g. `local mins, maxs = GridNav.GetBounds()`​

---

## `GridNav.GetGridIndex(x, y)`​

* Returns the grid index at `x`​ and `y`​ (grid-space)

---

## `GridNav.GetGridPoint(index)`​

* Returns grid-space coordinates for `index`​ as a Vector
* e.g. `local point = GridNav.GetGridPoint(GridNav.GetGridPoint(125, 50))`​

---

## `GridNav.GridToWorld(point)`​

* Converts `point`​ (Vector) to world-space coordinates as a Vector

---

## `GridNav.WorldToGrid(point)`​

* Converts `point`​ (Vector) to grid-space coordinates as a Vector

---

## `GridNav.GetLinePath(start, end)`​

* Returns a list of grid indices (use `GetGridPoint`​) for the straight path from start to end
* ​`start`​

  * Start point in world space
* ​`end`​

  * End point in world space

---

## `GridNav.IsLineClear(start, end)`​

* Returns whether a straight line can connect start and end
* ​`start`​

  * Start point in world space
* ​`end`​

  * End point in world space

---

## `GridNav.GetPath(start, end)`​

* Returns `path, is_clear`​

  * A list of grid indices (use `GetGridPoint`​) for the A\* shortest path from start to end
  * Also returns a boolean `is_clear`​
* ​`start`​

  * Start point in grid space
* ​`end`​

  * End point in grid space
* We believe Dota uses something closer to Theta\*, but this is a close enough approximation for now
* For more information: [Wikipedia](https://en.wikipedia.org/wiki/A*_search_algorithm)
