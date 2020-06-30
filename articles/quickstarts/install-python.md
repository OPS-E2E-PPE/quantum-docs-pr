---
title: Develop with Q# and Python
author: bradben
ms.author: bradben
ms.date: 5/30/2020
ms.topic: article
ms.custom: how-to
uid: microsoft.quantum.install.python
---

# Develop with Q# and Python

Install the QDK to develop Python host programs to call Q# operations.

1. Prerequisites

    - [Python](https://www.python.org/downloads/) 3.6 or later
    - The [PIP](https://pip.pypa.io/en/stable/installing) Python package manager
    - [.NET Core SDK 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)


1. Install the `qsharp` package, a Python package that enables interop between Q# and Python.

    ```
    pip install qsharp
    ```

1. Install IQ#, a kernel used by Jupyter and Python that provides the core functionality for compiling and executing Q# operations.

    ```dotnetcli
    dotnet tool install -g Microsoft.Quantum.IQSharp
    dotnet iqsharp install
    ```

    > [!NOTE]
    > If you get an error during the `dotnet iqsharp install` step, open a new terminal window and try again.
    > If this still doesn't work, try locating the installed `dotnet-iqsharp` tool (on Windows, `dotnet-iqsharp.exe`) and running:
    > ```
    > /path/to/dotnet-iqsharp install --user --path-to-tool="/path/to/dotnet-iqsharp"
    > ```
    > where `/path/to/dotnet-iqsharp` should be replaced by the absolute path to the `dotnet-iqsharp` tool in your file system.
    > Typically this will be under `.dotnet/tools` in your user profile folder.
  
1. While you can use Q# with Python in any IDE, we highly recommend using Visual Studio Code (VS Code) IDE for your Q# + Python applications. With the QDK Visual Studio Code extension you gain access to richer functionality such as warnings, syntax highlighting, project templates, and more.

    If you would like to use VS Code:

    - Install [VS Code](https://code.visualstudio.com/download) (Windows, Linux and Mac)
    - Install the [QDK extension for VS Code](https://marketplace.visualstudio.com/items?itemName=quantum.quantum-devkit-vscode).

    If you would like to use a different editor, the instructions above have you all set. 

1. Verify the installation by creating a `Hello World` application

    - Create a minimal Q# operation, by creating a file called `Operation.qs`, and adding the following code to it:

        ```qsharp
        namespace HelloWorld {
            open Microsoft.Quantum.Intrinsic;
            open Microsoft.Quantum.Canon;

            operation SayHello() : Unit {
                Message("Hello from quantum world!");
            }
        }
        ```

    - Create a Python program called `hello_world.py` to call the Q# `SayHello()` operation:

        ```python
        import qsharp

        from HelloWorld import SayHello

        SayHello.simulate()
        ```

    - Run the program:

        ```
        python hello_world.py
        ```

    - Verify the output. Your program should output the following lines:

        ```
        Hello from quantum world!
        ```


> [!NOTE]
> * You can also use Python Jupyter notebooks to write the classical Python program and call Q# operations from the cells. The Python code is just a normal Python program.

## Next steps

Now that you have installed the Quantum Development Kit in your preferred environment, you can write and run [your first quantum program](xref:microsoft.quantum.quickstarts.qrng).
