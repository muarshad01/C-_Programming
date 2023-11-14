## 265. Section Overview

* What is lambda expression?
    - Motivation
    - Review of function objects (functors)
    - Relation between lambdas and function objects

* Structure of lambda expression
* Types of lambda expressions
    - Stateless lambda expression
    - Stateful lambda expression (capturing context)
* Lambdas and the STL

***

## 266. Motivation

* Prior to C++ 11
    - Function objects
    - Function pointers

```c++
class Multiplier {
private:
    int num {};
public:
    Multiplier(int n) : num {n} {}
    int operator()(int n) const {       // operator()
        return num * n;
    }
};
```

* overloaded function called `operator()`
* whenever this operator `()` is used, the function associated with this 
operator `()` is called for an object of any Multiplier type.

```c++
std::vector<int> vec {1,2,3,4};
Multiplier mult {10};

std::transform(vec.begin(), vec.end(), mult);

//vec now contains {10,20,30,40}
```


```c++
template <typename T>
struct Displayer {
    void operator() (const T &data) {
        std::cout << data << " ";
    }
};
```
* template class to create a generic Displayer
* We can use this with function objects of any type that overload the insertion operator (`<<`)
* All we're doing is overloading the function call `operator()` to display a `T` object to `cout`.

```c++
Displayer<int> d1;
Displayer<std::string> d2;

d1(100);                // d.operator(100);
                        // displays 100

d2("Frank");            // d.operator("Frank");
                        // displays Frank
```
* Note, this example really shows clearly that `d1` and `d2` are objects, but we're using them like functions, and that's the reason they're called function objects.
***
* Lambdas replace function objects

* We write less code and more focused code
    - Best practice: When we have one or few statements of code; If we have more statements use function objects

***

## 267. Structure of Lambda

```c++
[] () -> return_type specifiers {};
```

```c++
[] () { std::cout << "Hi"; };
```
* A simple lambda expression

```c++
[] (int x) { std::cout << x; };
[] (int x, int y) { std::cout << x+y; };
```

```c++
auto l = [] () { std::cout << "Hi"; };
l();        // Displays Hi

l(10);      // displays 10
l(100);     // displays 100
```
***

## 268. Stateless Lambda Expressions

```c++
[] () { std::cout << "Hi";}();

[] (int x) { std::cout << "Hi";}(100);
```

```c++
const int n {3};
int nums[n] {10,20,30};

auto sum = [] (int nums[], int n) {
    int sum {0};
    for (int i = 0; i < n; i++)
        sum += nums[i];
    return sum;
};

std::cout << sum(nums, 3)
```

### Using lambda expressions as function parameters
```c++
#include <functional>

void foo(std::function<void(int)> l) {
    l(10)
}

OR

void foo(void (*l)(int)) {
    l(10);
}

OR

void foo(auto l) {
    l(10)
}
```

### Returning lambda expressions from functions

```c++
std::function<void(int)> foo() {
    return [] (int x) { std::cout << x; };
}

OR

void (*foo()) (int) {
    return [] (int x) { std::cout << x;};
}

OR

auto foo() {
    return [] (int x) { std::cout << x; };
}
```

### Using lambda expressions as predicates

```c++
void print_if(std::vector<int> nums, bool (*predicate)(int)) {
    for (int i : nums)
        if (predicate(i))
            std::cout << i;
}

int main() {
    std::vector<int> nums {1, 2, 3};
    
    print_if(nums, [] (auto x) { return x % 2 == 0; };);
    print_if(nums, [] (auto x) { return x % 2 != 0; };);
    return 0;
}
```
* predicate lambda passes as a function pointer
* a predicate is a c++ function that takes any number of arguments and returns
a boolean value. So, naturally it follows that a predicate lambda is a lambda that implements this function.
* predicate lambdas are extremely important when using the standard template library functions and algorithms such as `sort` of `for_each` which require a predicate parameter.
***

## 269. Stateless Lambda Expression Demo - Part 1

***

## 270. Stateless Lambda Expression Demo - Part 2

***

## 271. Stateful Lambda Expressions

***

## 272. Stateful Lambda Expressions Demo - Part 1

***

## 273. Stateful Lambda Expressions Demo - Part 2

***

## 274. Lambdas and the STL

***


