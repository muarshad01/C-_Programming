## 36. Section Overview

* Basic Components
* Preprocessor Directive
* The `main()` function
* Namespaces
* Comments
* Basic I/O

***

## 37. Overview of the Structure of a C++ Program

[C++ keywords](https://en.cppreference.com/w/cpp/keyword)

* Keywords in different languages:
    - C++    ~ 90
    - Java   ~ 50
    - C      ~ 32
    - Python ~33

* E.g., `int` and `return` are keywords.

* There is difference b/w `identifier` and `keywords`.
* Identifiers:
    - `include`, `std`, `cout`, `cin`, `endl` are identifiers.
    - An identifier is something that a programmer names. These names have been created by programmers to create something that represents something meaningful to them.

* Non-standard Operators(`<<`, `>>`, `::`) vs Standard Operators(`+`, `x`,`-`, `/`):
    - `<<` - stream insertion operator
    - `>>` - stream extraction operator
    - `::` - scope resolution operator
***

## 38. `#include` Pre-processor Directive 

* C++ Pre-processor:
    - A program that processes your source-code before the compiler sees it.
    - The C++ pre-processor first strips all the comments from the source file and replaces each comment with a single space. Then it looks for pre-processor directives and executes them.
    - Pre-processor directives are lines in the source code that being with a pound(`#`).
    - Commonly used to conditionally-compile source code.

```c++
#include
```

```c++
#if
#elif
#else
#endif
```

```c++
#ifdef
#ifndef
#define
#undef
```

```c++
#line
#error
#pragma
```
***

## 39. Comments

***

## 40. The `main()` function

```c++
int main(){
    // code
    
    return 0;
}
```

OR

```c++
int main(int argc, char *argv[]){
    // code

    return 0;
}
```

* `argc` - argument count
* `argv` - argument value
***

## 41. Namespaces

* Code is combination of three things:
    - 1. Our own code + 
    - 2. C++ std libraries and their code + 
    - 3. Libraries from third-party developers and their code.
* We can run into `naming conflict`.
* C++ allow developers to use `namespaces as containers` to `group code entities into a namespace scope`.

```c++
using namespace std;            # using namespace directive
```

```c++
using std::cout;                # qualified using namespace variant
using std::cin;
using std::endl;
```

***

## 42. Basic Input and Output (I/O) using `cin` and `cout`

* `cout`, `cin`, `cerr`, `clog`

### Exercise 1

### Exercise 2

### Exercise 3

***
