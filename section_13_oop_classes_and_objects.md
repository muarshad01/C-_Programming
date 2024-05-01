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
    std::string name {"Player"};
    int health {100};
    int xp {3};

    // methods
    void talk(std::string text_to_say);
    bool is_dead();
};
```

```c++
int main() {
    // `local objects` are created on `STACK MEMORY`.
    Player frank;
    Player hero;

    Player players[] = {frank, hero};

    vector<Player> player_vec{frank};
    player_vec.push_back(hero);

    // creating an object dynamically on `HEAP MEMORY` using the 'new' operator
    Player *enemy {nullptr};
    enemy = new Player;       

    // When you're finished using enemy object, its storage has to be freed up using 'delete'
    delete enemy;

    return 0;
}                   
```

```c++
class Account {
    // attributes
    std::string name {"Account"};
    double balance {0.0};

    // methods
    bool withdraw(double amount);
    bool deposit(double amount);
};
```

```c++
int main() {
    Account frank_account;
    Account jim_account;

    // An array of Account objects
    Account accounts [] {frank_account, jim_account};   

    // standard vector of account objects
    std::vector<Account> account_vec {frank_account};     
    account_vec.push_back(jim_account);

    Account *mary_account {nullptr};
    mary_account = new Account();

    delete mary_account;
}
```

***

## 138. Accessing Class Members

```c++
Account *account = new Account();

// Dereference the pointer then use the dot operator
(*account).balance
(*account).deposit(1000.00)

// Or use the member of pointer operator (arrow operator)
account->balance
account->deposit(1000.00)
```

```c++
Player *enemy = new Player
(*enemey).name = "Enemy";
(*enemey).health = 100;
enemey->xp = 15;

enemey->talk("I will destroy you!"); 
```
***

## 139. public and private

* `public`
    * accessible everywhere
* `private`
    * accessible only by members or friends of the class
* `protected`
    * used with inheritence

```c++
class Player {
private:
    // attributes
    std::string name;
    int health;
    int xp;
public:
    // methods
    void talk(std::string text_to_say);
    bool is_dead();
};
```

```c++
Player frank;
frank.name = "Frank";            // compiler error
frank.healt = 1000;              // compiler error
frank.talk("Ready to battle")    // ok

Player *enemy = new Player();
enemy-> = 100;                  // compiler error
enemy->talk("Hello");           // ok

delete enemy;
```

***

## 140. Implementing Member Methods

* Very similar to how we implemented functions

* `Member methods (instance methods)` have access to `member attributes (instance attributes)`
    - So you don't need to pass them as arguments

* Can be implemented inside the class declaration
    - `Implicitly inline`

* Can be implemented outside the class declaration
    - Need to use `ClassName::method_name`

* Can separate `specification` from `implementation`
    - `.h`  file for the class declaration
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
    // methods declared INLINE
    void set_balance(double bal) {
        balance = bal;
    }

    double get_balance() {
        return balance;
    }

    // methods to be declared OUTSIDE the class declaration
    void set_name(std::string n);
    string get_name();
    
    bool deposit(double amount);
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
    if(balance - amount >= 0) {
        balance -= amount;
        return true;
    } else {
        return false;
    }
}
```

***

## 141. Constructor and Destructors

* Special member method
* Invoked during `object creation`
* Useful for initialization
* Same name as the class
* No return type is specified
* Can be overloaded

### Destructors

* Same name as the class preceeded with a tilde (`~`)
* Invoked automatically when an `object is destroyed`
* No return type and no parameters
* Only `1` destructor is allowed per class - `cannot be overloaded`
* Useful to release memory and other resources

```c++
class Player {
private:
    std::string name;
    int health;
    int xp;
public:
    // Overloaded Constructors
    Player();
    Player(std::string name);
    Player(std::string name, int health, int xp);

    // Destructor
    ~Player();
};
```

```c++
{
    Player slayer;
    Player frank {"Frank", 100, 4};
    Player hero {"Hero"};
    Player villain {"Villain"};
    // use the 4 objects
} // 4 destructor are called
```
* All of above 4 objects are `LOCAL OBJECTS` and they'll be created on `STACK`.
* When the block `{...}` ends, these objects go out-of-scope and their destructor will be called automatically.

```c++
Player *enemy = new Player("Enemy", 100, 0);
delete enemy;   // destructor called
```

```c++
class Account {
private:
    std::string name;
    double balance;
public:
    // Constructors
    Accout();
    Account(std::string name);
    Account(double balance);
    Account(std::string name, double balance);

    // Destructor
    ~Account();
};
```

***

## 142. The Default Constructor

* Doesn't expect any arguments
    - Also called `no-args constructor`
* If you write no constructor at all for a class
    - C++ will generate a `Default Constructor` that does nothing
* Called when you instantiate a new object with no arguments
```c++
Player frank;
Player *enemy = new Player;
```
### Using the default constructor

```c++
class Account {
private:
    std::string name;
    double balance;
public:
    bool withdraw(double amount);
    bool deposit(double amount);
};
```

```c++
// creating two LOCAL OBJECTS (on STACK) frank_account and jim_account
Account frank_account;
Account jim_account;

Account *mary_account = new Account;
deletecmary_account;
```

### User-defined no-args constrcutor
```c++
class Account {
private:
    std::string name;
    double balance;
public:
    Account() {
        name = "None";
        balance = 0.0;
    }
    bool withdraw(double amount);
    bool deposit(double amount);
};
```

### No default constructor
```c++
class Account {
private:
    std::string name;
    double balance;
public:
    Account(std::string name_val, double bal) {
        name = name_val;
        balance = bal;
    }
    bool withdraw(double amount);
    bool deposit(double amount);
};
```

```c++
// creating two LOCAL OBJECTS frank_account and jim_account
Account frank_account;                      // Error
Account jim_account;                        // Error

Account *mary_account = new Account;        // Error
delete mary_account;

Account bill_account {"Bill", 15000.0};     // OK
```

***

## 143. Overloading Constructors

* Classes can have as many constructors as necessary
* Each must have a `unique signature`
* `Default constructor is no longer compiler-generated once another constructor is declared`

```c++
Player::Player() {
    name = "None";
    health = 0;
    xp = 0;
}

Player::Player(std::string name_val) {
    name = name_val;
    health = 0;
    xp = 0;
}

Player::Player(std::string name_val, int health_val, int xp_val) {
    name = name_val;
    health = health_val;
    xp = xp_val;
}

Player empty;                                   // None, 0, 0
Player here {"Hero"};                           // Hero, 0, 0
Player villain {"Villain"};                     // Villain, 0, 0
Player frank {"Frank", 100, 4};                 // Frank, 100, 4

Player *enemy = new Player("Enemy", 1000, 0);   // Enemy, 1000, 0
delete enemy;
```

***

## 144. Constructor Initialization lists

```c++
// Previous way:
Player::Player() {
    name = "None";          // assignment not initialization
    health = 0;
    xp = 0;
}

// Better way:
Player::Player() 
    : name{"None"}, health{0}, xp{0} {
}
```

```c++
// Previous way:
Player::Player(std::string name_val) {
    name = name_val;                    // assignment not initialization
    health = 0;
    xp = 0;
}

// Better way:
Player::Player(std::string name_val) 
    : name{name_val}, health{0}, xp{0} {
}
```

```c++
// Previous way:
Player::Player(std::string name_val, int health_val, int xp_val) {
    name = name_val;          // assignment not initialization
    health = health_val;
    xp = xp_val;
}

// Better way:
Player::Player(std::string name_val, int health_val, int xp_val) 
    : name{name_val}, health{health_val}, xp{xp_val} {
}
```
***

## 145. Delegating Constructors

* Often the code for constructors is very similar
* Duplicating code can lead to errors
* C++ allows delegating constructors
    - code for one constructor can call another in the initialization list
    - avoids duplicating code

```c++
Player::Player() 
    : name{"None"}, health{0}, xp{0} {
}

Player::Player(std::string name_val) 
    : name{name_val}, health{0}, xp{0} {
}

Player::Player(std::string name_val, int health_val, int xp_val) 
    : name{name_val}, health{health_val}, xp{xp_val} {
}

// Delegating Constructures
Player::Player() 
    : Player {"None", 0, 0} {
}

Player::Player(std::string name_val) 
    : Player {name_val, 0, 0} {
}

Player::Player(std::string name_val, int health_val, int xp_val) 
    : name{name_val}, health{health_val}, xp{xp_val} {
}
```

***

## 146. Constructor Parameters and Default Values


```c++
class Player {
private:
    std::string name;
    int health;
    int xp;
public:
    // constructor with default parameter value
    Player(std::string name = "None",
        int health = 0,
        int xp = 0);
};
```

***

## 147. Copy Constructor

* When objects are copied C++ must create a new object from an existing object

* When is a copy of an object made
    - 1 passing object by value as a parameter
    - 2 returning an object from a function by value
    - 3 constructing one object based on another of the same class

* C++ must have a way of accomplishing this so it provides a compiler-defined copy constructor if you don't

### 1 Passing object by value as a parameter
```c++
Player hero {"Hero", 100, 20};

void display_player(Player p) {
    // p is a COPY of hero in this example
    // use p
    // Destructor for p will be called
}

display_player(hero);
```
### 2. Returning an object from a function by value
```c++
Player enemy;

Player create_super_enemy() {
    Player an_enemy{"Super Enemy", 1000, 1000};
    return an_enemy;    // A COPY of an_enemy is returned
}

enemy = create_super_enemy();
```

### 3 constructing one object based on another of the same class
```c++
Player hero {"Hero", 100, 100};

Player another_hero {hero};     // A COPY of hero is made
```

* Beware if you have a pointer data member
    - Pointer will be copied
    - Not what it is pointing to
    - `Shallow versus Deep copy` - more in the next video

### Best practices
* Provide a copy constructor when your class has raw-pointer-data-members
* Provide the copy constructor with a `const` reference parameter
* USE STL classes as they already provide copy constructors
* Avoid using raw-pointer-data-members if possible

```c++
Type::Type(const Type &source);
Player::Player(const Player &Player);
Account::Account(const Account & Account)
```

```c++
Player::Player(const Player &source) 
    : name{source.name}, health{source.health}, xp{source.xp} {
    // : Player {source.name, source.health, source.xp} {
}
```

```c++
Account::Account(const Account &source) 
    : name{source.name}, balance{source.balance} {
}
```

***

## 148. Shallow Copying with the Copy Constructor

* Consider a class that contains a pointer as a data member
* Constructor allocates storage dynamically and initialized the pointer
* Destructor releases the memory allocated by the constructor
* What happens in the default copy constructor

### Default copy constructor
* memberwise copy
* Each data member is copied from the source object
* The pointer is copied NOT what it points to (shallow copy)
* **PROBLEM**: When we release the storage in the destructor, the other object still refers to the released storage.

```c++
class Shallow
{
private:
    int *data;                          // Pointer
public:
    Shallow(int d);                     // Constructor
    Shallow(const Shallow &source);     // COPY Constructor
    ~Shallow();                         // Destructor
};
```

```c++
Shallow::Shallow(int d) {
    data = new int;                    // allocate storage
    *data = d;
}
```

```c++
Shallow::~Shallow() {
    delete data;                       // free storage
}
```

***

## 149. Deep Copying with the Copy Constructor

* Create a copy of the pointed-to data
* Each copy will have a pointer to unique storage in the heap
* Deep copy when you have a raw pointer as a class data member

```c++
class Deep {
private:
    int *data;                      // POINTER
public:
    Deep(int d);                    // Constructor
    Deep(const Deep &source)        // Copy Constructor
    ~Deep();                        // Destructor
};
```

```c++
Deep::Deep(int d) {
    data = new int;                 // allocate storage
    *data = d;
}
```

```c++
Deep::~Deep() {
    delete data;                    // free storage
    cout << "Destructor freeing data" << endl;
}
```

### Copy Constructor
```c++
Deep::Deep(const Deep &source) {
    data = new int;                 // allocate storage
    *data = *source.data;
    cout << "Copy constructor - deep" << endl;
}
```

```c++
Deep::Deep(const Deep &source) 
    : Deep{*source.data} {
        cout << "Copy constructor - deep" << endl;
}
```

* Delegate to `Deep(int)` and pass in the `int (*source.data)` source is pointing to

***

## 150. Move Constructors

* R-value reference operator(`&&`)

***

## 151. The `this` Pointer

***

## 152. Using `const` with Classes

* Pass arguments to class member methods as `const`
* We can also create `const` objects
* What happens if we call member functions on `const` objects?
* `const`-correctness

```c++
const Player villain {"Villain", 100, 55};

villain.set_name("Nice guy");                   // ERROR

std::cout << villain.get_name() << std::end;    // ERROR
```

```c++
const Player villain {"Villain", 100, 55};

void display_player_name(const Player &p) {
    cout << p.get_name() << endl;
}

display_player_name(villain);       // ERROR
```

```c++
class Player {
private:
    ...
public:
    std:string get_name() const;
    ...
};
```


***

## 153. Static Class Members

***

## 154. Structs vs Classes

* In addition to define a `class` we can declare a `struct`
* `struct` come from the C programming language
* Essentially the same as a `class` except
    - members are `public` by default

```c++
class Person {
    std::string name;
    std::string get_name();
};

Person p;
p.name = "Frank";               // compiler error
std::cout << p.get_name();      // compiler error
```

```c++
struct Person {
    std::string name;
    std::string get_name();
};

Person p;
p.name = "Frank";               // OK - public
std::cout << p.get_name();      // OK - public
```

* `struct`
    - Use `struct` for passive objects with public access
    - Don't declare methods in `struct`
* `class`
    - Use class for active objects with private access
    - Implement getters / setters as needed
    - Implement member methods as needed

***

## 155. Friends of a class


***

## 156. Section Challenge

***

## 157. Section Challenge - Solution

***












































