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

```c++
class Base {
    // Base class members...
};

class Derived : access-specifier Base {
    // Derived class members
};
```
* Access-specifier can be: `public`, `private`, or `protected`

* `public`
    - Most common
    - Established `is-a` relationship between Derived and Base classes
* `private` and `protected`
    - Establishes "derived class has a base class" relationship

```c++
class Account {
    // Account class members...
};

class Savings_Account : public Account {
    // Saving_Account class members...
};
```
* Saving_Account `is-a` Account

```c++
Account account {};
Account *p_account = new Account();

account.deposit(1000.0);
p_account->withdraw(200.0)

delete p_account;
```

***

## 173. Protected Members and Class Access

***

## 174. Constructors and Destructors

```c++
class Base {
public:
    Base(){ cout << "Base constructor" << endl; }
    ~Base(){ cout << "Base destructor" << endl; }
};

class Derived : public Base {
public:    
    Derived(){ cout << "Derived constructor" << endl; }
    ~Derived(){ cout << "Derived destructor" << endl; }
};
```

***

## 175. Passing Arguments to Base Class Constructors

```c++
class Derived : public Base {
    int doubled_value;
public:
    Derived() : Base {}, double_value{0} {
        cout << "Derived no-args constructor " << endl;
    }
    Derived(int x) : Base {x}, double_value{x*2} {
        cout << "int Derived constructor " << endl;
    }
};
```

***

## 176. Copy / Move Constructors and Operator = with Derived Classes

```c++
class Derived : public Base {
    int doubled_value;
public:
    // Same constructors as previous example

    Derived(const Derived &other)
        : Base(other), doubled_value {other.doubled_value} {
            cout << "Derived copy constructor " << endl;
    }
};
```

```c++
class Base {
    int value;
public:
    // Same constructors as previous example
    Base &operator=(const Base &rhs) {
        if (this != &rhs) {
            value = rhs.value;
        }
        return *this;
    }
};
```

```c++
class Derived : public Base {
    int doubled_value;
public:
    
    Derived &operator=(const Derived &rhs) {
        if (this != &rhs) {
            Base::operator(rhs);                // Assign Base part
            doubled_value = rhs.doubled_value;  // Assign Derived part
        }
        return *this;
    }
};
```

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










