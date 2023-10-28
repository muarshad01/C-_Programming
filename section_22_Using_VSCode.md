## 275. Section Overview

***

## 280. Installing VSCode on Mac OSX

* Extensions -> search codelldb -> Install `CodeLLDB`

***

## 281. Building and Running C++ Programs with VSCode on Mac OSX

* Extensions -> search codelldb -> Install `CodeLLDB`

* View -> Command Palette -- OR --> `shift + command + p` -> search C++ -> C/C++ Edit Configuration (UI)
- Compiler path -> select `/usr/bin/g++`
- C++ standard -> select c++17


* select `main.cpp` -> Terminal -> Configure Default Build Task -> select `compiler: /usr/bin/g++`
    - update `tasks.json`:
```
"args": [
      "-fdiagnostics-color=always",
      "-g",
->    "-Wall",                         # Tell the compiler to generate all warnings.
->    "--std=c++17",
->	  "${fileDirname}/*.cpp",
	  "-o",
	  "${fileDirname}/${fileBasenameNoExtension}"
],
```
    - save with `command + s`


* select `main.cpp` -> Terminal -> Run Build Task
* select `main` -> right-click -> Open in Integrated Terminal
***

## 282. Debugging C++ Programs with VSCode on Mac

***

## 283. Using the Course Source Code with VSCode on Mac

***

##
