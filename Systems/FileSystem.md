# FileSystem

This table contains functions that allow traversing the game's files.

* [FileSystem.FindFirst](https://hake.me/docs/systems/filesystem#filesystem-findfirst-wildcard)

---

## `FileSystem.FindFirst(wildcard)`​

**This API is very slow! The results should be cached, or only be used when necessary.**

### Arguments

* ​`wildcard`​ - The filename pattern to search for

  * e.g. `"*"`​ or `"*.vsnd_c"`​

### Returns

A `handle`​ and `name`​ for a file search result

* e.g. `local handle, name = FileSystem.FindFirst("*")`​
* ​`handle`​ has a metatable:

  * ​`handle:IsDirectory()`​

    * Returns true if this result is a directory
  * ​`handle:Next()`​

    * Advances the handle to the next result in the search, and returns the name of the result
    * e.g. `name = handle:Next()`​
    * If this returns `nil`​, the handle is no longer valid and the end of the search has been reached
  * ## `handle:Close()`​

    * ## **Required to be called when you are done using this handle**
    * If this is not called, a deadlock may occur within the game
