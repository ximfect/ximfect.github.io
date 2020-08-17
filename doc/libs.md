# ximfect Lib Reference

## Lib Structure
Like effects, all of the lib's files are stored in a folder whose name will be the lib's ID.
The ID is used with the `Require` function to load libs.
The lib will automatically load all `.js` files present in it's directory when `Require`d.

The only file a lib needs to work is an `effect.yml` file, with the following fields:

* `name` -> the lib's DISPLAY name
* `version` -> a semantic version of the lib 
* `author` -> the name and email of the creator
* `desc` -> a description of the effect

Example:
```yml
name: Cool lib
version 4.2.0
author: Very cool guy <verycool@guy.com>
desc: Contains some cool utilities
```
