[Beginning C++ Programming - From Beginner to Beyond](https://www.udemy.com/course/beginning-c-plus-plus-programming/) -- 10/27/2023

***
# Sections

* [Section 02: Installation and Setup](https://github.com/muarshad01/CPP_Programming/blob/main/section_02_installation_and_setup.md) -- 09/27/2023
* [Section 22: Using VSCode](https://github.com/muarshad01/CPP_Programming/blob/main/section_22_Using_VSCode.md)

***

# Other

* [Run C++ and C in Visual Studio Code](https://www.youtube.com/watch?v=3-9sObAg6R0)
* [How to Run C++ in VSCode on MacOS](https://www.youtube.com/watch?v=tdAD0WZjXrM)
    - Open VSCode, we need to install two extensions:
        - 1. Extensions -> search c/c++ -> Install `C/C++ IntelliSense`, ... 
        - 2. Extensions -> search code runner -> Install `Code Runner` (22 million downloads)
        - 3. Extensions -> search code codelldb -> Install `CodeLLDB`
    - Make sure you have a compiler installed
        - `Terminal` -> `$ clang --version`
        ```
            Apple clang version 14.0.3 (clang-1403.0.22.14.1)
            Target: arm64-apple-darwin22.6.0
            Thread model: posix
            InstalledDir: /Library/Developer/CommandLineTools/usr/bin
        ```
        - `Terminal` -> `$ gcc` / `$ g++` -> `clang: error: no input files`
        - Otherwise, install `$ xcode-select --install`
        - Write `hello.cpp` -> Run (compiler: /usr/bin/g++)
            - DEBUG CONSOLE
            - TERMINAL `$ ./hello` 
***

```
$ g++ --std=c++11 hello.cpp
```

***

# 283. Using the `Course Source Code` with `VSCode` on `MacOS`

## STEP-1 (Setup `IntelliSense`)

* `main.cpp` -> View -> `Command Palette` OR `cmd + shift + p` -> search C++ -> `C/C++: Edit Configuration (UI)`
    - Compiler path: `/usr/local/g++`
    - C++ standard: `c++17`

We can see that `.vscode` folder is created with `{} c_cpp_properties.json` file

## STEP-2 (Setup `Default Build Task`)

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




