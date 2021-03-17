# How to install/share effects & libs

[<< Back to index](../index.md)

## Installing effects

1. In your Command Prompt/Terminal, navigate to the location of the effect
    package you downloaded (`.fx.xpk` file).

2. If your effect(s) is in an `.fx.xpk` file, use the `ximfect unpack-effect`
    command to automatically unpack and install the effect.

    Example:

    ```sh
    ximfect unpack-effect invert.fx.xpk
    ```

    If your effect(s) is in a `.zip` file, unzip it first using an external
    program, and then install the resulting `.fx.xpk` files.

## Installing libs

Installing libs is largely the same as installing effects, except libs come in
`.lib.xpk` files, and instead of `ximfect unpack-effect`,
`ximfect unpack-lib` is used.

Example:

```sh
ximfect unpack-lib math.lib.xpk
```

## Sharing effects/libs

To pack your effect into a package anyone else can easily install, use the
`ximfect pack-effect` command. It will produce a `.fx.xpk` file you can share
and others can use to install the effect.

Example:

```sh
ximfect pack-effect invert
```

Same can be done with libs: instead of `ximfect pack-effect`, `ximfect pack-lib`
is used, and a `.lib.xpk` file is produced.

Example:

```sh
ximfect pack-lib math
```
