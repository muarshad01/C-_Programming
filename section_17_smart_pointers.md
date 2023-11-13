## 196. Section Overview

* C++ Smart Pointers
- Unique pointers (`unique_ptr`)
- Shared pointers (`shared_ptr`)
- Weak pointers (`weak_ptr`)
- Auto pointers (`auto_ptr`)    // DEPRECATED
***

## 197. Some Issues with Raw Pointers

* Some potentially serious problems
    - Uninitialized (wild) pointers
    - Memory leaks
    - Dangling pointers
    - Not exception safe

***

## 198. What is a Smart Pointer? Ownership and RAII

* Objects
* Can only point to heap-allocated memory
* Automatically call `delete` when no longer needed
* ---
* Defined by class templates
    - Wrapper around a raw pointer

```c++
{   
    std::smart_pointer<Some_Class> ptr = ...
    
    ptr->method();
    cout << (*ptr) << endl;

    // ptr will be destroyed automatically
    // when no longer needed
}
```

***

## 199. Unique Pointers

***

## 200. Shared Pointers

***

## 201. Weak Pointers

***

## 202. Custom Deleters

***

## 203. Section Challenge 1

***

## 204. Section Challenge 1 - Solution

***















