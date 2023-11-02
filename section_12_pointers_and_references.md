## 116. Section Overview

***

## 117. What is a Pointer?

***

## 118. Declaring Pointers

```c++
variable_type *pointer_name;
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
* If you don't initialize a pointer to pint to a variable or function then you should initialize it to `nullptr` to **make it mull**
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

***

## 124. Const and Pointers

***

## 125. Passing Pointers to Functions

***

## 126. Returning a Pointer from a Function

***

## 127. Potential Pointer Pitfalls

***

## 128. What is a Reference

***

## 129. L-values and R-values

***

## 130. Using the `CodeLite` IDE Debugger

***

## 131. Section Recap

***

## 132. Section Challenge

***

## 133. Section Challenge - Solution

***











































