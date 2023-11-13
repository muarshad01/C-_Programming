## 53. Section Overview

***

## 54. What is an Array

***

## 55. Declaring and Initializing Arrays

```c++
int test_scores [5] {100,95,99,87,88};

int high_score_per_level [10] {3,5};        // init to 3,5 and remaining to 0

const double days_in_year {365};
double hi_temperatures [days_in_year] {0};      // init all to zero

int another_array [] {1,2,3,4,5};       // size automatically calculated
```

***

## 56. Accessing and Modifying Array Elements

* The name of the array represents the location of the first element in the array (index 0)
* The `[index]` represents the offset from the beginning of the array
***

## 57. Multidimensional Arrays

int movie_rating [3][4]
{
    { 0, 4, 3, 5},
    { 2, 3, 3, 5},
    { 1, 4, 4, 5}
};
***

## 58. Declaring and Initializing Vectors

```c++
vector <char> vowels {'a', 'e', 'i', 'o', 'u'};

vector <int> test_scores {100, 98, 89, 95, 93};

vector <double> hi_temperatures (365, 80.0)         // (fixed_size, all_values_initialized_to)
```

***

## 59. Accessing and Modifying Vector Elements

```c++
vector_name.at(element_index)

test_scores.at(1)
```

```c++
vector<vector<int>> movie_ratings
{
    {1, 2, 3, 4},
    {1, 2, 4, 4},
    {1, 3, 4, 5}
};
```

***

## 60. Section Challenge

***

## 61. Section Challenge - Solution

***








