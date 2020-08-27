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
    # On Linux:
    go build -o ../ximfect

    # On Windows:
    go build -o ..\ximfect.exe
    ```
