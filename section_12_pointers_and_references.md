## 116. Section Overview
* What is a pointer?
    * A variable whose value is an address

***

## 117. What is a Pointer?

***

## 118. Declaring Pointers

```c++
variable_type *pointer_name {nullptr};
```

```c++
int *int_ptr;
double *double_ptr;
char *char_ptr;
string *string_ptr;
```

```c++
variable_type *pointer_name {nullptr};
```

```c++
int *int_ptr {};
double *double_ptr {nullptr};
char *char_ptr {nullptr};
string *string_ptr {nullptr};
```

* Always initialize pointers
* Uninitialized pointers contain garbage data and can point `anywhere`
* Initializing to zero of `nullptr` represents address zero
   * implies that the pointer is pointing `nowhere`
* If you don't initialize a pointer to point to a variable or function then you should initialize it to `nullptr` to **make it null**

***

## 119. Accessing the Pointer Address and Storing Address in a Pointer

* (`&`) the address operator

```c++
int num {10};
cout << "The value of num is: " << num << endl;         // 10
cout << "sizeof num is: " << sizeof(num) << endl;       // 4
cout << "Address of num is: " << &num << endl;          // 0x61ff1c
```

```c++
int *p;
cout << "Value of p is: " << p << endl;                 // 0x61ff60 - garbage
cout << "Address of p is: " << &p << endl;              // 0x61ff18
cout << "sizeof p is: " << sizeof(p) << endl;           // 4

p = nullptr;                                            // set `p` to point nowhere

cout << "Value of p is: " << p << endl;                 // 0
```

* Don't confuse the size of a pointer and the size of what it points to
* All pointers in a program have the same size

```c++
int *p1 {nullptr};
double *p2 {nullptr};
unsigned long long *p3 {nullptr};
vector<string> *p4 {nullptr};
string *p5 {nullptr};
```

* The compiler will make sure that the address stored in a pointer variable is of the correct type
* pointers are variables so they can change

***

## 120. Dereferencing a Pointer

* Access the data we're pointing to - dereferencing a pointer

* You can access the data at the address contained in the `score_ptr` using the dereferencing operator (`*`)

```c++
int score {100};
int *score_ptr {&score};

cout << *score_ptr << endl;     // 100

*score_ptr = 200;
cout << *score_ptr << endl;     // 200
cout << score << endl;          // 200
```

***

## 121. Dynamic Memory Allocation

* We can allocate storage for a variable at run time
    - For arrays, we explicitly provide size and it was fixed
    - But vectors, grow and shrink dynamically 

* We can use pointers to `access newly allocated heap storage`

```c++
int *int_ptr {nullptr};

int_ptr = new int;          // allocate an integer on heap

cout << int_ptr << endl;    // 0x2747f28

cout << *int_ptr << endl;   // 41188049 - garbage

*int_ptr = 100;

cout << *int_ptr << endl;   // 100

delte int_ptr;              // frees the allocated storage
```

```c++
int *array_ptr {nullptr};
size_t size {0};

cout<< "How big do you want the array?";
cin >> size;

array_ptr = new int[size];      // allocate array on the heap

...

delete [] array_ptr;            // free allocated storage
```

***


## 122. The Relationship Between Arrays and Pointers

* The value of `array_name` is `the address of the first element in the array`
* The value of `pointer variable` is an `address`
* If the pointer points to the-same-data-type-as-the-array-element (`int *score_ptr {scores};`) then the pointer and array name can be used interchangeably (almost)

```c++
int scores[] {100, 95, 89};

cout << scores << endl;         // 0x61fec8
cout << *scores << endl;        // 100

int *score_ptr {scores};

cout << score_ptr << endl;      // 0x61fec8
cout << *score_ptr << endl;     // 100
```

***

## 123. Pointer Arithmetic

```c++
cout << *score_ptr << endl;
score_ptr++;

OR

*score_ptr++;
```

```c++
int scores[]{100, 95, 89, 68, -1};
int *score_ptr {scores}

while(*score_ptr != -1) {
    cout << *score_ptr << endl;
    score_ptr++;
}

cout << "\n-----------" << endl;

score_ptr = scores;
while(*score_ptr != -1) {
    cout << *score_ptr++ << endl;
}
```

***

## 124. Const and Pointers

### Pointers to constants
* The `data pointed to by the pointers` is constant and **cannot** be changed.
* The pointer itself can be changed and can point somewhere else.

```c++
int high_score {100};
int  low_score {205};

const int *score_ptr = { &high_score };

*score_ptr = 86;                // ERROR
 score_ptr = &low_score;        // OK
```
* Constant pointers
* Constant pointers to constants

### Constant pointers
* The `data pointed to by the pointers` can be changed.
* The pointer itself **cannot** change-and-point somewhere else.

```c++
int high_score {100};
int  low_score {205};

int *const score_ptr = { &high_score };

*score_ptr = 86;                // OK
 score_ptr = &low_score;        // ERROR
```
### Constant-pointers to constants
* The `data pointed to by the pointer` is constant and **cannot** be changed.
* The pointer itself **cannot** change-and-point somewhere else.

```c++
int high_score {100};
int  low_score {205};

const int *const score_ptr = { &high_score };

*score_ptr = 86;                // ERROR
 score_ptr = &low_score;        // ERROR
```
***

## 125. Passing Pointers to Functions

* Pass-by-reference with pointers - defining the function

* The function parameter is a pointer
* The actual parameter can be a pointer or address-of-variable

```c++
void double_data(int *int_ptr);

void double data(int *int_ptr) {
    *int_ptr *= 2;
}
```

```c++
int main() {
    int value {10};

    cout << value << endl;      // 10

    double_data( &value );      // address of variable
    
    cout << value << endl;      // 20
}
```

```c++
#include <iostream>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x{100}, y{200};

    cout << "\nx:" << x << endl;
    cout << "\y:"  << x << endl;
    
    swap(&x, &y);

    cout << "\nx:" << x << endl;
    cout << "y:"   << x << endl;

    return 0;
}
```

```c++
void display(const std::vector<string> *const v) {
    for(auto str : *v)
        cout << str << "";
    cout << endl;
}
```

***

## 126. Returning a Pointer from a Function

* Functions can also return pointers
```c++
type *function();
```

```c++
int *largest_int(int *int_ptr1, int *int_ptr2) {
    if (*int_ptr1 > *int_ptr2)
        return int_ptr1;
    else
        return int_ptr2; 
}

int main() {
    int a{100};
    int b{200};

    int *largest_ptr {nullptr};
    largest_ptr = largest_int(&a, &b);
    cout << *largest_ptr << endl;
    return 0;
}
```

### Returning dynamically allocated memory

```c++
int *create_array(size_t size, int init_value = 0) {
    
    int *new_storage {nullptr};

    new_storage = new int[size];

    for (size_t i{0}; i < size; ++i)
        *(new_storage + i) = init_value;
    
    return new_storage;
}
```

```c++
int main() {
    int *my_array;                      // Will be allocated by the function

    my_array = create_array(100, 20);   // Create the array

    ...

    delete [] my_array;                 // Be sure to free space
    
    return 0;
}
```

### Never return a pointer to a local variable
```c++
int *dont_do_this () {
    int size {};
    ...
    return &size;
}

int *or_this () {
    int size {};
    int *int_ptr {&size};
    ...
    return int_ptr;
}
```

***

## 127. Potential Pointer Pitfalls

### Uninitialized pointers
```c++
int *int_ptr;       // pointing anywhere

*int_ptr = 100;     // Hopefully a crash
```

### Not checking if `new` failed
* If `new` fails an exception is thrown
* We can use exception handling to catch exceptions
* Dereferencing a null-pointer will cause your program to crash

### Dangling pointer
* Pointer that is pointing to released memory
    - For example, 2 pointers point to same data
    - 1 pointer releases the data with `delete`
    - The other pointer accesses the release data
* Pointer that points to memory that is valid
    - We saw this when we returned a pointer to a function local variable

### Leaking memory
* Forgetting to release allocated memory with `delete`
* If you lose your pointer to the storage allocated on the heap you have no way to get to that storage again
* The memory is orphaned or leaked
* One of the most common pointer problems
***

## 128. What is a Reference

* An alias for a variable
* Must be initialized to a variable when declared
* Cannot be null
* Once initialized cannot be made to refer to a different variable
* Very useful as function parameters
* Might be helpful to thin of a reference as a constant pointer that is automatically dereferences
### Using references in range-based for loop
```c++
vector<string> stooges {"Larry", "Moe", "Curly"};

for (auto str : stooges) {
    str = "Funny";                  // changes the copy
}

for (auto str : stooges) {
    cout << str << endl;            // Larry, Moe, Curly
}
```

```c++
vector<string> stooges {"Larry", "Moe", "Curly"};

for (auto &str : stooges) {         // Notice `&str`
    str = "Funny";                  // `&str` is a reference to each vector element
}

for (auto str : stooges) {
    cout << str << endl;            // Funny, Funny, Funny
}
```

```c++
for (auto const &str : stooges) {   // Notice `const` keyword
    str = "Funny";                  // Now the `vector` elements have changed
}
```
***

## 129. L-values and R-values

```c++
int square(int &n) {
    return n*n;
}

int num {10};

square(num);        // OK
```

***

## 130. Using the `CodeLite` IDE Debugger

***

## 131. Section Recap

***

## 132. Section Challenge

***

## 133. Section Challenge - Solution

***











































