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












































