## 43. Section Overview

* What are constant?
* Declaring constants
* Literal constants
* Constant expressions

***

## 44. What is a variable?

A variable is an abstraction for a memory location

***

## 45. Declaring and Initializing Variables

```c++
int age;

int age = 21;       // C-like initialization

int age = (21)      // Constructor initialization

--> int age {21};  // C++11 list-initialization style
```

***

## 46. Global Variables

* Global variables are automatically initialized to `zero`.

***

## 47. C++ Built-in Primitive Types

* Size and precision is often compiler-dependent.

### Character Types
```c++
char
char16_t
char32_t
wchar_t
```

### Integer Types
```c++
signed short int            #`signed short` OR just `short` i.e., need not put `int`
signed int
signed long int
signed long long int

unsigned short int
unsigned int
unsigned long int
unsigned long long int
```

### Floating-point Type
```c++
float
double
long double
```
***

## 48. What is the Size of a Variable(`sizeof` operator)

* `sizeof(char)`

* `sizeof(short)`
* `sizeof(int)`
* `sizeof(long)`
* `sizeof(long long)`

* `sizeof(float)`
* `sizeof(double)`
* `sizeof(long double)`

* `sizeof(unsigned int)`

* `sizeof(some_variable)`
* `sizeof some_variable`

* `<climits>`
    -  CHAR_MIN / CHAR_MAX
    -  SHRT_MIN / SHRT_MAX
    -   INT_MIN / INT_MAX
    -  LONG_MIN / LONG_MAX
    - LLONG_MIN / LLONG_MAX

* `<cfloat>`
    - FLT_MIN / FLT_MAX
***

## 49. What is a Constant?

***

## 50. Declaring and Using Constants

* Literal constants
* Declared constants (`const` keyword)
* Constant expressions(`constexpr` keyword)
* Enumerated constants (`enum` keyword)
* Defined constants (`#define`)

### Integer Literal Constants
* 12   - an integer
* 12U  - an unsigned integer
* 12L  - a long integer
* 12LL - a long long integer

### Floating-point Literal Constants
* 12.1  - a double
* 12.1F - a float
* 12.1L - a long double

### Character Literal Constants
***

## 51. Section Challenge

***

## 52. Section Challenge - Solution

Quiz 3: Section 06 Quiz

***

















