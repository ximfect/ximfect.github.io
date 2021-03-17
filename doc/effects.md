# Effect Reference

[<< Back to index](../index.md)

## Effect Structure

A ximfect Effect is a folder in the `APPDATA/ximfect/effects` directory (usually
`C:\Users\<your username>\AppData\ximfect\effects` on Windows;
`/home/<your username>/ximfect/effects` on Unix). The folder's name will be the
effect ID you use in the CLI to refer to the effect. Such a folder must contain
two files:

* `effect.lua` -> the effect's main script. Look below for an explaination.
* `effect.yml` -> the effect's metadata. Look below for an explaination

If either of those files are missing, ximfect will be unable to load the effect.

**It is strongly recommened that you know Lua and YAML before you make effects
for ximfect.**

### Effect script (`effect.lua`)

As the heading might suggest, this is the main script of the effect. All effects
are defined in the `effect` function. It will be called once for every pixel in
the image given to ximfect. The effect function takes 1 parameter, which is the
pixel in question and returns 1 value, which is the new colour of that same
pixel.

Pixels are represented as Lua tables with the following values:

* `x`, `y` -> the X and Y coordinates of the pixel respectively. You don't have
to specify this in the return value. (You can find it in the input pixel.)
* `r`, `g`, `b`, `a` -> the RGBA color values of the pixel. You must return all
4 of them, otherwise you'll get an error.

Below is an example effect that inverts the colour of all pixels:

```lua
function effect(pixel)
  return {
    r = 255 - pixel["b"], -- because we use 8-bit color, we can simply subtract
    g = 255 - pixel["g"], -- our pixel values from the maximum possible value,
    b = 255 - pixel["r"], -- that being 255.
    a = 255 - pixel["a"]
  }
end
```

ximfect also provides you with a public API inside of the effect. The API is a
set of function you can use in your code for the effect.

Below is a list of all of these functions:

* `arg(name: string) -> string | bool | nil`:
  
  If name is a valid argument name that was passed to ximfect, if that argument
  is a valued argument, it's value is returned as a string. If it is a boolean
  argument (doesn't have value) however, it's value is returned as a boolean. If
  no argument with the given name was found, `nil` is returned.

* `at(x: int, y: int) -> Pixel`:
  
  Returns the pixel at the specified `x` and `y` coordinates in the image. If
  the coordinates are bigger than the image, they "loop over". (e.g. If the
  image is 100 pixel across in both directions, and we want the pixel at x=120
  y=10, it'll return the pixel at x=20 y=10)

* `size() -> Point`:
  
  Returns the size of the image as a table with `x` and `y` fields.

* `import(name: string) -> void`:
  
  Loads the given lib.

* `random() -> float`:
  
  Returns a random float between 0.0 and 1.0.

* `randint(max: int) -> int`:
  
  Returns a random integer between 0 and `max - 1`.

* `inspect(value: value) -> void`:
  
  Prints some information about the given value.

* `int(value: value) -> int`:
  
  Returns the given value as an integer.

* `debug(message: string) -> void`:
  
  Sends a debug-level message to the log.

* `info(message: string) -> void`:
  
  Sends a info-level message to the log.

* `warn(message: string) -> void`:
  
  Sends a warn-level message to the log.

### Effect metadata (`effect.yml`)

The effect metadata is contained in the `effect.yml` file. YAML is a rather
simple and easy to read format, so it shouldn't be too hard to write the such a
file for your effect.

Below is a list of fields for the metadata:

* `name: string`
  
  A **display** name for your effect. This is not the same as the effect ID.
  This is can only be seen by using the `ximfect about-effect` command, and
  nowhere else.

* `version: Version`:
  
  A semantic version number of the effect.

* `author: Author`:
  
  Your name aswell as an e-mail to contact you. For example:
  `John Doe <me@johndoe.com>`

* `desc: string`:
  
  A short description of what your effect does.

* **optional** `preload: List<string>`:
  
  A list of files to be executed before the effect is ran. The names written
  here are names of files *in your effect folder*.

Below is an example of what such a file might look like:

```yaml
name: Invert
version: 1.0.0
author: John Doe <me@johndoe.com>
desc: Inverts the color of the image.
```
