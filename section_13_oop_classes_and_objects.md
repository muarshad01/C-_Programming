## 134. Section Overview

***

## 135. What is OOP?

***

## 136. What are Classes and Objects?

***

## 137. Declaring a Class and Creating Objects

```c++
class Player {
    // attributes
    std::string name;
    int health;
    int xp;

    // methods
    void talk(std::string to_to_say);
    bool is_dead();
};
```

```c++
Player frank;
Player hero;

Player *enemy = new Player();       // creating an object dynamically on head using `new`

delete enemy;                       // When I'm finished using enemy object, its storage has to be freed up using `delete`
```

```c++
class Account {
    // attributes
    std::string name;
    double balance;

    // methods
    bool withdraw(double amount);
    bool deposit(double amount);
};
```

```c++
Account frank_account;
Account jim_account;

Account accounts [] {frank_account, jim_account};   // An array of Account objects

Account *mary_account = new Account();
delete mary_account;

std::vector<Account> accounts1 {frank_account};     // standard vector of account objects
accounts1.push_back(jim_account);
```

***

## 138. Accessing Class Members

***

## 139. public and private

***

## 140. Implementing Member Methods

* Very similar to how we implemented functions

* Member methods have access to member attributes
    - So you don't need to pass them as arguments!

* Can be implemented inside the class declaration
    - Implicitly inline

* Can be implemented outside the class declaration
    - Need to use Class_name::method_name

* Can separate specification from implementation
    - `.h` file for the class declaration
    - `cpp` file for the class implementation

File `Account.h` has **specification**:
```c++

#ifndef _ACCOUNT_H_
#define _ACCOUNT_H_

class Account {

private:
    // attributes
    std::string name;
    double balance;

public:
    // methods
    // declared IN-LINE
    void   set_balance(double bal) { balance = bal; }
    double get_balance() { return balance; }

    // methods will be declared OUTSIDE the class declaration
    void   set_name(std::string n);
    string get_name();
    
    bool  deposit(double amount);
    bool withdraw(double amount);
};

#endif      // _ACCOUNT_H_
```

* Note, some compiler use `#pragma once` insted as well. See the documentation.

File `Account.cpp` has **implementation**:

```c++
#include "Account.h"

void Account::set_name(std::string n) { 
    name = n;
}

string Account::get_name() { 
    return name;
}

bool Account::deposit(double amount) {
    balance += amount;
    return true;
}

double Account::withdraw(double amount) {
    if(balance-amount >= 0) {
        balance -= amount;
        return true;
    } else {
        return false;
    }
}
```

***
***

## 141. Constructor and Destructors

***

## 142. The Default Constructor

***

## 143. Overloading Constructors

***

## 144. Constructor Initialization lists

***

## 145. Delegating Constructors

***

## 146. Constructor Parameters and Default Values

***

## 147. Copy Constructor

***

## 148. Shallow Copying with the Copy Constructor

***

## 149. Deep Copying with the Copy Constructor

***

## 150. Move Constructors

***

## 151. The `this` Pointer

***

## 152. Using `const` with Classes

***

## 153. Static Class Members

***

## 154. Struct vs Classes

***

## 155. Friends of a class

***

## 156. Section Challenge

***

## 157. Section Challenge - Solution

***












































