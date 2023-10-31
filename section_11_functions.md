## 101. Section Overview

***

## 102. What is a Function?

* Modularization of program.
    - More modular, more readable, more maintainable
    - Information hiding
    - Abstraction

* [C++ Standard Library headers](https://en.cppreference.com/w/cpp/header)

* `<cmath>`
    - [Standard library header <cmath>](https://en.cppreference.com/w/cpp/header/cmath)

* `<cstdlib>`
    - [Standard library header <cstdlib>](https://en.cppreference.com/w/cpp/header/cstdlib)

```c++
size_t count {10};
int min {1};
int max {6};

srand(time(nullptr))

for(size_t i{1}; i<=count; ++i){
    random_number = rand() % max + min;
    cout << random_number << endl;
}

```
***

## 103. Function Definition

* called BEFORE it is defined ERROR

***

## 104. Function Prototypes

* Use function prototypes
    - Tell the compiler what it needs to know without a full function definition
    - Also called `forward declarations`
    - Placed at the beginning of the program
    - Also used in our own head files(`.h`) - more about this later

***

## 105. Function Parameters and the return Statement

* function call - `arguments`
* function definition - `parameters`

### pass-by-value

* When you pass data into a function it is passed-by-value
* A copy of the data is passed to the function
* Whatever changes you make to the parameter (formal parameter) in the function doesn't affect the argument that was passed in.

* Formal parameter
    - The parameters defined in the function header
* Actual parameter
    - The parameters used in the function call, the arguments
    - In c++, the actual parameters are passed-by-value or copied to formal parameters

```c++
void param_test(int formal){    // formal is a copy of actual
    cout << formal << endl;     // 50    
    formal = 100;               // only change the local copy
    cout << formal << endl;     // 100
}

int main(){
    int actual {50};            
    cout << actual << endl;     // 50
    param_test(actual);         // pass in 50 to param_test
    cout << actual << endl;     // 50 - didn't change
    return 0; 
}
```

```c++
void print_vector(vector<string> v) {
    for(auto s: v) {
        cout << s << " ";
    }
    cout << endl;
}
```

***

## 106. Default Argument Values

* Default values can be in the prototype or definition, not both
    - best practice - in the prototype
    - must appear at the tail end of the parameter list
* Can have multiple default values
    - must appear consecutively at the tail end of the parameter list

```c++
#include <iomanip>

cout << fixed << setprecision(2)
```
***

## 107. Overloading Functions

* We can have function that have different parameter lists that have the same name
* Abstraction mechanism since we can just think `print` for example
* A type of `polymorphism`
    - We can have the `same-function-name` work with `different-data-types` to execute similar behavior
* The compiler must be able to tell the functions apart based on the parameter lists and argument supplied 
***

## 108. Passing Arrays to Functions

***

## 109. Pass by Reference

***

## 110. Scope Rules

***

## 111. How do Function Calls Work?

***

## 112. Inline Functions

***

## 113. Recursive Functions

***

## 114. Section Challenge

***

## 115. Section Challenge - Solution

***

