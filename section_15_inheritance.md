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

***

## 171. Inheritance vs. Composition

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










