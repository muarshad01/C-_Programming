[Beginning C++ Programming - From Beginner to Beyond](https://www.udemy.com/course/beginning-c-plus-plus-programming/) -- 10/27/2023

***

# Sections


## PART-1

* [Section 01: Introduction]()
* [Section 02: Installation and Setup](https://github.com/muarshad01/CPP_Programming/blob/main/section_02_installation_and_setup.md) -- 09/27/2023
* [Section 03: Curriculum Overview]()
* [Section 04: Getting Started](https://github.com/muarshad01/CPP_Programming/blob/main/section_04_getting_started.md) -- 09/28/2023
* [Section 05: Structure of C++ Program](https://github.com/muarshad01/CPP_Programming/blob/main/section_05_structure_of_a_c%2B%2B_program.md) -- 09/30/2023
* [Section 06: Variables and Constants]()
* [Section 07: Arrays and Vectors]()
* [Section 08: Statements and Operators]()
* [Section 09: Controlling Program Flow]() -- skip
* [Section 10: Characters and Strings]()
* [Section 11: Functions]()
* [Section 12: Pointers and References]()

## PART-2

* [Section 13: OOP - Classes and Objects]()
* [Section 14: Operator Overloading]()
* [Section 15: Inheritance]()
* [Section 16: Polymorphism]()
* [Section 17: Smart Pointers]()

## PART-3

* [Section 18: Exception Handling]()
* [Section 19: I/O and Streams]()
* [Section 20: The Standard Template Library (STL)]() -- skip
* [Section 21: Lambda Expressions]()
* [Section 22: Using VSCode](https://github.com/muarshad01/CPP_Programming/blob/main/section_22_Using_VSCode.md) -- 09/28/2023
* [Section 23: Enumerations]()

***

## `VSCode` Extensions for `C++`

* [Run C++ and C in Visual Studio Code](https://www.youtube.com/watch?v=3-9sObAg6R0)
* [How to Run C++ in VSCode on MacOS](https://www.youtube.com/watch?v=tdAD0WZjXrM)
    - Open `VSCode`, we need to install TWO extensions:
        - 1. Extensions -> search c/c++ -> Install `C/C++ IntelliSense` 
        - 2. Extensions -> search code codelldb -> Install `CodeLLDB`

### Check if compiler is installed
```        
$ clang --version
```

```
Apple clang version 14.0.3 (clang-1403.0.22.14.1)
Target: arm64-apple-darwin22.6.0
Thread model: posix
InstalledDir: /Library/Developer/CommandLineTools/usr/bin
```

```        
$ gcc -> clang: error: no input files
$ g++ -> clang: error: no input files
```

Otherwise, install using: `$ xcode-select --install` 

***

```
$ g++ --std=c++11 hello.cpp
```

***

## 283. Using the `Course Source Code` with `VSCode` on `MacOS`

### STEP-1 (Setup `IntelliSense`)

* `main.cpp` -> View -> `Command Palette` OR `cmd + shift + p` -> search C++ -> `C/C++: Edit Configuration (UI)`
    - Compiler path: `/usr/local/g++`
    - C++ standard: `c++17`

We can see that `.vscode` folder is created with `{} c_cpp_properties.json` file

### STEP-2 (Setup `Default Build Task`)

* Terminal -> Configure `Default Build Task` (compiler: `/usr/bin/g++`)

We can see that `{} tasks.json` file is created. Edit and update it as follows:

```json
"args": [
    "-fdiagnostics-color=always",
    "-g",
->    "-Wall",
->    "-std=c++17",
->    "${fileDirname}/*.cpp",
    "-o",
    "${fileDirname}/${fileBasenameNoExtension}"
],
```

### Step-3 (RUN the code)

* `main.cpp` -> Terminal -> `Run Build Task` (`shift + command + b`)
* `main` -> right-click `Open in Integrated Terminal`

### Step-4 (DEBUG)

* `main.cpp` -> Run -> `Add Configuation` -> `C++ (GDB/LLDB)`

This will create `{} launch.json` file. Edit and update it as follows:

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "g++ - Build and debug active file",
            "type": "lldb",
            "request": "launch",
            "program": "${fileDirname}/${fileBasenameNoExtension}",
            "args": [],
            "cwd": "${fileDirname}",
            "preLaunchTask": "C/C++: g++ build active file"
        }
    ]
}
```

***
