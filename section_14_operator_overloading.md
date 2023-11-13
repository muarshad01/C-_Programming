## 158. Section Overview

* Overloading the assignment operator (`=`)
    - Copy semantics
    - Move semantics

* Overloading stream insertion (`<<`) and extraction operators (`>>`)

***

## 159. What is Operator Overloading

```c++
class MyString {
private:
    char *str;      // C-style string
public:
    MyString();                         // no-args constructor 
    MyString(const char *s);            // overloaded constructor
    MyString(const MyString &source);   //copy constructor

    ~MyString();
    void display const;
    int get_length() const;
    const char *get_str() const;
};
```

```c++
int main() {
    MyString empty;             // no-args constructor
    MyString larry("Larry");    // overloaded constrctor
    MyString stooge {larry};    // copy constructor
    ...
}
```

```c++
// No-args constructor
MyString::MyString()
    : str(nullptr) {
    str = new char[1];
    *str = '\0';
}

// Overloaded constructor
MyString::MyString(const char *s)
    : str(nullptr) {
    if(s == nulptr){
        str = new char[1];
        *str = '\0';
    } else {
        str = new char[std::strlen(s)+1];
        std::strcpy(str,s);
    }
}

// Copy constructor
MyString::MyString(const MyString &source)
    : str(nullptr) {
    str = new char[std::strlen(source.str)+1];
    std::strcpy(str, source.str);
}

// Destructor
MyString::~MyString {
    delete [] str;
}
```

***

## 160. Overloading the Assignment Operator (copy)

***

## 161. Overloading the Assignment Operator (move)

***

## 162. Overloading Operators as Member Functions

***

## 163. Overloading Operators as Global Functions

***

## 164. Overloading the Stream Insertion and Extraction Operators

***

## 165. Section Challenge

***

## 166. Section Challenge - Solution 1

***

## 167. Section Challenge - Solution 2

***














