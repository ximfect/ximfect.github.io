# ximfect Effect Reference

## Effect Structure
All effects are stored in a folder, whose name will be the effect's ID.
The effect's ID is use to indentify the effect, for example in the CLI.

Here is the structure needed for an effect to work. All files will be explained below.
```
(your effect id)
|- effect.js
|- effect.yml
```

### effect.js
This file contains JavaScript code of the effect.
This file's contents are ran once before the effect itself is applied.
The effect is applied by calling the `effect` function on each pixel of the input image.

The file must define an `effect` function with 3 parameters:

* `x`: `int` -> the x position of the current pixel
* `y`: `int` -> the y position of the current pixel
* `pixel`: `RGBAPixel` -> the RGBA values of the pixel

The `effect` function must return a `RGBAPixel`-like object, containing 4 `int` properties: `r`, `g`, `b` and `a`.

Example:
```js
function effect(x, y, pixel) {
  return {r: pixel.r*2, g: pixel.g/2, b: pixel.b*pixel.b, a: pixel.a};
}
```

### effect.yml
This file describes the effect.

Required fields:

* `name` -> the effect's DISPLAY name
* `version` -> a semantic version of the effect
* `author` -> the name and email of the creator
* `desc` -> a description of the effect

Optional fields:

* `preload` -> an array of filenames to load before initially running the `effect.js` file

Example:
```yml
name: Example effect
version: 1.2.3
author: Example Guy <guy@example.com>
desc: Does some cool things
```

## Effect API
ximfect provides a couple of funtions to interact with the image from the `effect.js` file.
They are described below.

### `RGBAPixel ImageAt(int x, int y)`
Retrieves and returns the RGBAPixel at `x`,`y` from the image.

### `Size ImageSize()`
Returns the image's size.

### `void Require(string lib)`
Essentially executes all of a lib's files in the current context.
