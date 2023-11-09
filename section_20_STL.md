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

***
