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

```c++
void print_array(int numbers []);
```

* Since the `array name` evaluates to the `location of the first element` of array in memory - this address is what is copies
* So the function has no idea how many elements are in the array since all it know sit the `location of the first element` (`the name of the array`)
***

## 109. Pass by Reference

* Sometimes we want to be able to change the `actual parameter` from within the function body

* In order to achieve this, we need the location or `address (&)` of the actual parameter

* We saw how this is the effect with array, but what about other variable types?

* We can use `reference parameters` to tell the compiler to pass in a reference to the `actual parameter`

* The `formal parameter` will now be alias for the `actual parameter`
***


```c++
void print(const std::vector<int> &v){  // Look there is a `const` and `&v`
    v.at(0) = 200;                      // ERROR
    for (auto num : v) {
        cout << num << end;
    }
}
```

```c++
void pass_by_ref3(vector<string> &v){   // Notice: There is no `const`
    v.clear()
}
```

## 110. Scope Rules

* C++ uses `scope rules` to determine where an identifier can be used
* C++ used `static` of lexical scoping
    - scope is determined the same way you read the program
* `Local` of `Block {}` scope
* Global scope


* Local variables are NOT preserved between function call

### Static Local Variables
* Declared with `static` qualifier
```c++
static int value {10};
```
* Value is preserved between function calls
* Only initialized the first time the function is called.

### Global scope
* Global constants are OK
* Best practice - don't use global variables

```c++
void local_example(int x){
    int num {1000};
    cout << "\nLocal num is" << num << endl;
    num = x;
    cout << "\nLocal num is" << num << endl;
}

local_example(10);
local_example(20);
```
* Everytime we call the function `local_example()`, the local variable `num` is initialized to `1000`.


```c++
int num {300};                  // Global variable - declared outside any class or variable

void global_example() {
    cout << "\nGlobal num is" << num << endl;
    num *= 2;
    cout << "\nLocal num is" << num << endl;
}

global_example();
global_example();
```


```c++
void static_local_example(){
    static int num {5000};
    cout << "\nLocal static num is" << num << endl;
    num += 1000;
    cout << "\nLocal static num is" << num << endl;
}

static_local_example();
static_local_example();
```
* `static int num {5000}` will be initialized the first time function is called. After that it retains it s value.

* `static int num` behaves like a global variable, however, its scope is local.

***

## 111. How do Function Calls Work?

***

## 112. Inline Functions

```c++
incline int add_numbers(int a, int b) {     // Note keyword `inline`
    return a + b
}

int main() {
    int result {0};
    result = add_numbers(100, 200);
    return 0;
}
```

***

## 113. Recursive Functions

***

## 114. Section Challenge

***

## 115. Section Challenge - Solution

***

