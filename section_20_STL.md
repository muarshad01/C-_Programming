## 237. Section Overview

***

## 238. What is STL?

* A library of powerful, reusable, adaptable, generic classes and functions

* Assortment of commonly used containers

* Consistent, fast, and `type-safe`

* Extensible

```c++
#include <vector>
#include <algorithm>

std::vector<int> v {1,5,3};

std::sort(v.begin(), v.end());

for (auto elem : v)
    std::cout << elem << std::endl;

std::reverse(v.begin(), v.end));

for (auto elem : v)
    std::cout << elem << std::endl;

int sum{};

sum = std::accumulate(v.begin(), v.end(), 0);
std::cout << sum << std::endl;

```

***

## 239. Generic Programming with Macros

* Generic programming: Writing code that works with a variety of types as arguments, as long as those argument meet specific syntactic and semantic requirements.

* Function templates

* Class templates

```c++
#define MAX(a, b) ((a > b) ? a : b)

std::coud << MAX(10, 20)   << std::endl;
std::coud << MAX(2.5, 3.5) << std::endl;
std::coud << MAX('A', 'C') << std::endl;
```

* Macros ***beware***
```c++
#define SQUARE(a) a*a

#define SQUARE(a) ((a)*(a))
```

***

## 240. Generic Programming with Function Templates

* We need to tell the complier this is a template function
* We also need to tell it that `T` is the template parameter

```c++
template <typename T>
T max(T a, T b) {
    return (a > b) ? a : b;
}
```

* We may also use `class` instead of `typename`

```c++
template <class T>
T max(T a, T b) {
    return (a > b) ? a : b;
}
```

```c++
int a {10};
int a {20};

std::cout << max<int>(a, b);
```

* Many times the compiler can deduce the type and the template parameter is not needed

```c++
std::cout << max<double>(c, d);

std::cout << max(c, d);
```

* The following will not compiler unless `Player` overloads `operator>`

```c++
Player p1{"Hello", 100, 20};
Player p2{"Enemy", 99, 14};

std::cout << max<Player>(p1, p2);
```

* We can have multiple template parameters
```c++
template <typename T1, typename T2>
void func(T1 a, T2 b) {
    std::cout << a << " " << b;
}
```

```c++
func<int, double>(10, 20.2);

func('A', 12.4);
```

```c++
struct Person {
    std::string name;
    int age;
    bool operator<(const Person &rhs) const {
        return this->age < rhs.age;
    }
};

Person p1 = {"Curly", 15};
Person p2 = {"Moe", 30};

Person p3 = min(p1, p2);
```

```c++
std::ostream &operator<<(std::ostream &os, const Person &p) {
    os << p.name;
    return os;
}
```

```c++
template <typename T>
void swap(T &a, T &b) {
    temp = a;
    a = b;
    b = temp;
}
```

***

## 241. Generic Programming with Class Templates

* Similar to function template, but at the class level
* Allows plugging-in any data type


```c++
class Item {
private:
    std::string name;
    int value;
public:
    Item(std::string name, int value)
        : name{name}, value{value}
    {}
    std::string get_name() const { return name;}
    int get_value() const {return value; }
};
```

* But we'd like our `Item` class to be able to hold any type of data in addition to the string
* We can't overload class names
* We don't want to use `dynamic polymorphism`

[std::pair](https://en.cppreference.com/w/cpp/utility/pair)
```c++
#include <utility>

std::pair<std::string, int> p1 {"Frant", 100};
std::cout << p1.first;  // Frank
std::cout << p1.second; // 100
```

[std::array](https://en.cppreference.com/w/cpp/container/array)

***

## 243. Introduction to STL Containers

* Each container has member functions
    - Some are specific to the container
    - Others are available to all containers
* Each container has an associated header file
    - `#include <container_type>`
***

## 244. Introduction to STL Iterators

* Iterators must be declared based on the container type they will iterate over

```c++
container_type::iterator_type iterator_name
```

```c++
std::vector<int>::iterator it1;
std::list<std::string>::iterator it2;
std::map<std::string, std::string>::iterator it3;
std::set<char>::iterator it4;
```

```c++
std::vector<int> vec {1,2,3};

std::vector<int>::iterator it = vec.begin();

OR

auto it = vec.begin()


for (auto it = vec.begin(); it != vec.end(); it++) {
    std::cout << *it << " ";
}

```

***

## 245. Introduction to Iterators - Demo

```c++
#include <vector>
#include <set>
#include <map>
#include <list>
```

***

# 246. Introduction to STL Algorithms

* Many algorithms require extra information in order to do their work
    - **Functors (function objects)**
    - Function pointers
    - Lambda expressions (C++11)

***

## 247. Introduction to Algorithms - Demo

```c++
class Person {
public:
    std::string name;
    int age;
private:
    Person() = default;
    Person()
        : name{name}, age{age}  {}
    bool operator<(const Person &rhs) const {
        return this->age < rhs.age;
    }
    bool operator==(const Person &rhs) const {
        return (this->name == rhs.name && this->age == rhs.age);
    }
};
```
***

## 248. Sequence Container - Array

* [Containers library](https://en.cppreference.com/w/cpp/container)

```c++
std::array<int,5> arr1 {2,1,4,5,3};

std::array<int,5>::iterator min_num = std::min_element(arr1.begin(), arr1.end());
                       auto max_num = std::max_element(arr1.begin(), arr1.end());
```

***

## 249. Sequence Containers - Vector

***

## 250. Sequence Containers - Deque

***

## 251. Section Challenge 1

***

## 252. Section Challenge 1 - Solution

***

## 253. Sequence Containers - List and Forward List

***



