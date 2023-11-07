## 182. Section Overview

***

## 183. What is Polymorphism?

* Ploymorphism
    - Compile-time / early binding / static binding
    - Run-time / late binding / dynamic binding
* Run-time polymorphism
    - Being able to assign different meanings to the same function at run-time
* Run-time polymorphism is achieved via
    - Inheritance
    - Base class pointers or references
    - Virtual functions

***

## 184. Using a Base Class Pointer

```c++
Account *p1 = new Account();
Account *p2 = new Account();
Account *p3 = new Account();
Account *p4 = new Account();

Account *array[] = {p1, p2, p3, p4};

for (auto i=0; i<4; ++i) {
    array[i] -> withdraw(1000);
}
```

```c++
Account *p1 = new Account();
Account *p2 = new Account();
Account *p3 = new Account();
Account *p4 = new Account();

vector<Account *> accounts
    {p1, p2, p3, p4};

for (auto acc_ptr : accounts) {
    acc_ptr -> withdraw(1000);
}

// delete the pointers
```
***

## 185. Virtual Functions

* Declare the function you want to override as virtual in the Base class
* Virtual functions are virtual all the way down the hierarchy from this point
* Dynamic polymorphism only via Account class pointer or reference 

```c++
class Account {
public:
    virtual void withdraw(double amount);
};
```

* Override the function in the Derived classes
* Function signature and return type must match EXACTLY
* virtual keyword not required but is best practice
* If you don't provide an overridden version it is inherited from it's base class

```c++
class Checking: public Account {
public:
    virtual void withdraw(double amount);
};
```
***

## 186. Virtual Destructors

* If a class has virtual functions
* ALWAYS provide a public virtual destructor
* If base class destructor is virtual then all derived class destructor are also virtual

```c++
class Account {
public:
    virtual void withdraw(double amount);
    virtual ~Account();
};
```

***

## 187. Using the `override` Specifier

***

## 188. Using the `final` Specifier

* When sued at the class level
    - Prevents class from being derived from

* When used at the method level
    - Prevents virtual method from being overridden in derived classes

```c++
class A {
public:
    virtual void do_something();
};

class B : public A {
    virtual void do_something() final;      // prevent further overriding
};

class C : public B {
    virtual void do_something();            // COMPILER ERROR - Can't override
};
```

***

## 189. Using Base Class References

***

## 190. Pure Virtual Functions and Abstract Classes

***

## 191. Abstract Classes as Interfaces

***

## 192. Section Challenge

***

## 193. Section Challenge - Solution Part 1

***

## 194. Section Challenge - Solution Part 2

***

## 195. Section Challenge - Final Solution

***
