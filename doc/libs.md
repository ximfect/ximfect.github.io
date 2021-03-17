# Lib Reference

[<< Back to index](../index.md)

## About libs

A ximfect Lib is a folder in the `APPDATA/ximfect/libs` directory (usually
`C:\Users\<your username>\AppData\ximfect\libs` on Windows;
`/home/<your username>/ximfect/libs`on Unix). The folder's name will be the lib
ID you use in the CLI and in the `import` function (see
[effect reference](effecs.md) if you're confused). Such a folder must one file:
`effect.yml`, which is the lib's metadata, as well as any `.lua` files
containing the lib's code.

When a lib is `import`ed, all of it's `.lua` files are executed. All of the
public API is available to these files, so youcould have a lib `import` another
lib.
