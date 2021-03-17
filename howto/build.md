# How to build ximfect yourself

[<< Back to index](../index.md)

## Prerquisites

* The Go Programming Langage (v 1.14+)

## Guide

1. Clone the ximfect repository:

    ```sh
    git clone https://github.com/ximfect/ximfect.git
    cd ximfect/src
    ```

2. Install dependecies

    ```sh
    go get ./...
    ```

3. Finally build ximfect

    ```sh
    # On Unix:
    go build -o ../ximfect

    # On Windows:
    go build -o ..\ximfect.exe
    ```

    Alternatively, you can use the more automated build script (Windows only):

    ```sh
    cd ..\testing
    build-test
    ```

    This will automatically increment the build number and regenerate the
    `src/tool/const.go` file to contain the new build information. It is
    recommended that you only use this if you're making contributions to
    ximfect.
