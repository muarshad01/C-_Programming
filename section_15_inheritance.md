## 168. Section Overview

***

## 169. What is Inheritance?

```c++
class Account {
    // balance, deposit, withdraw, ...
};

class Saving_Account {
    // balance, deposit, withdraw, interest_rate, ...
};

class Checking_Account {
    // balance, deposit, withdraw, minimum balance, per check fee, ...
};

class Trust_Account {
    // balance, deposit, withdraw, interest_rate, ...
};
```


```c++
class Account {
    // balance, deposit, withdraw, ...
};

class Saving_Account : public Account {
    // interest_rate, specialized withdraw, ...
};

class Checking_Account : public Account {
    // minimum balance, per check fee, specialized withdraw, ...
};

class Trust_Account : public Account {
    // interest_rate, specialized withdraw, ...
};
```
***

## 170. Terminology and Notation

* Base class (parent class, super class)
* Derived class (child class, sub class)

***

## 171. Inheritance vs. Composition

* Inheritance
    - `is-a` relationship
        - Employee `is-a` Person
        - Checking Account `is-a` Account
        - Circle `is-a` Shape
* Composition
    - `has-a` relationship
        - Person `has a` Account
        - Player `has a` Special Attack
        - Circle `has a` Location

```c++
class Person {
private:
    std::string name;       // has-a name
    Account account;        // has- account
};
```

***

## 172. Deriving Classes from Existing Classes

***

## 173. Protected Members and Class Access

***

## 174. Constructors and Destructors

***

## 175. Passing Arguments to Base Class Constructors

***

## 176. Copy / Move Constructors and Operator = with Derived Classes

***

## 177. Redefining Bases Class Methods

***

## 178. Multiple Inheritance

***

## 179. The Updated Accounts Example

***

## 180. Section Challenge

***

## 181. Section Challenge - Solution

***










