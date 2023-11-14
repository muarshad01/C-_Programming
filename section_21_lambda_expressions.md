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

* overloaded function called `operator()`
* whenever this operator `()` is used, the function associated with this 
operator `()` is called for an object of any Multiplier type.
```

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

***

## 268. Stateless Lambda Expressions

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


