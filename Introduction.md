# Introduction

# Introduction

Starting in early 2017 hake.me now supports making your own features through the use of its Lua scripting system.

## Lua language

The scripting system implemented by hake.me uses the [Lua](https://lua.org/) (version 5.3.4) programming language. If you are a developer interested in making your own features for hake.me then begin by familiarizing yourself with the Lua programming language, utilizing the resources available at [Lua.org](https://lua.org/).

## Installing scripts

If you are a user interested in using a premade Lua script you must first place the corresponding files in the correct directory so the hake.me software can find and load it for you. hake.me uses a simple system for installing scripts where the only requirement is to have created a `\scripts\`​ directory along side your `client.exe`​ where you will place the scripts after downloading them.

For instance if your `client.exe`​ is installed under the `C:\stuff\`​ directory, and you were interested in installing `AbilityAlert.lua`​ then you would lay out the files like the following:

* ​`C:\`​

  * ​`stuff\`​

    * ​`client.exe`​
    * ​`scripts\`​

      * ​`AbilityAlert.lua`​

You can uninstall scripts by removing them from the `\scripts\`​ directory.

## For developers

The way hake.me loads Lua scripts is by iterating all `.lua`​ files under the `\scripts\`​ directory. These Lua scripts are considered *top-level* because they reside in the top-most directory where scripts can exist. If you want to use more than one script for your feature (for instance if you want to seperate utility functions into their own file) then make a subdirectory in the `\scripts\`​ folder and place your other scripts in there so that they are no longer *top-level* and will not be automatically ran. This way you can `require(...)`​ them from their sub-directory. As it stands, all *top-level* scripts are considered to be distinct features on their own.

‍
