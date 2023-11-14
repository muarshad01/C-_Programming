## 93. Section Overview

* Character functions
* C-style Strings
* Working with C-style Strings
***
* C++ Strings
* Working with C++ Strings

```c++
#include <cctype>
```
* Functions for testing characters
* Functions for converting character case

* Character Functions
    - `isalpha(c)`
    - `isalnum(c)`
    - `isdigit(c)`
    - `islower(c)`
    - `isprint(c)`
    - `ispunct(c)`
    - `isupper(c)`
    - `isspace(c)`
    - `tolower(c)`
    - `toupper(c)`

```c++
char my_name[8];

my_name = "Frank";          // Error

strcpy(my_name, "Frank");   // OK
```

***

## 94. Character Functions

```c++
#include<cstring>

strcpy(str, "Hello ");  // copy

strcat(str, "there ");  // concatenate

cout << strlen(str);    // 11

strcmp(str, "Another");  // > 0

```

***

## 95. C-Style Strings

***

## 96. Working with C-Style Strings

***

## 97. C++ Strings

```c++
#include <string>
using namespace std;

string s1;                  // Empty
string s2 {"Frank"};        // Frank
string s3 {s2};             // Frank
string s4 {"Frank", 3};     // Fra
string s5 {s3, 0, 2};       // Fr
string s6 (3, 'X');         // XXX
```

```c++
string s1;
s1 = "C++ Rocks!";

string s2 {"Hello"};
s2 = s1;                // s2 will contain a copy of s1
```

***

## 98. Working with C++ Strings

***

## 99. Section Challenge

***

## 100. Section Challenge - Solution

***








