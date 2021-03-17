# The ximfect CLI

[<< Back to index](../index.md)

## Actions

The ximfect CLi is based on actions. Each action is tied to some unique function
of the program, and has a unique name as well as aliases. The action you wish
to execute is the first argument passed to ximfect. Actions range from something
simple, such as showing version or license information, to applying an effect to
an image or packing/unpacking an effect or lib.

## Positional vs named

The arguments you pass to ximfect are split into two different types, each with
their own quirks:

* Positional:

    All arguments passed back-to-back before the named arguments. You can only
    check the amount of positional arguments passed or whether a specific
    positional argument was passed. Generally, positional arguments are used
    for arguments that are required to be passed every time an action is ran.

* Named:

    Unlike postional arguments, named arguments are distinguished by their name,
    and not their position. Named arguments can be valued arguments or boolean
    arguments. Valued arguments have a specific value specified, whereas boolean
    arguments can only be true or false. They are generally used as optional
    arguments. They are also passed to the effect being currently executed.
    Whereas positional arguments are not.

## The `--debug` named argument

The `--debug` named argument is a boolean argument that can be added to the end
of any call to ximfect to enable DEBUG-level log messages to be shown. Unless
some unexpected error has occured, and you're trying to troubleshoot it, it's
mostly used during development.
