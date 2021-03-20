# How to build ximfect yourself

[<< Back to index](../index.md)

## Prerquisites

* Go 1.16+ [*Download*](https://golang.org/dl)
* Python 3.6+ [*Download*](https://python.org/downloads)

## Guide

1. Clone the ximfect repository:

    ```sh
    git clone https://github.com/ximfect/ximfect.git
    cd ximfect
    ```

2. Install dependecies

    ```sh
    cd src
    go get ./...
    ```

3. Finally build ximfect

    ```sh
    # this assumes you're in the `src` folder
    cd ..\testing
    
    # Windows
    py -3 build.py

    # Linux
    python3 build.py
    ```

    This script will automatically output a binary in the 'testing' folder.
    In case you can't run the resulting executable and you're on Linux, try
    using `chmod` to allow the file to be executed:

    ```sh
    chmod +x ./ximfect
    ```
