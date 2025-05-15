# Array (Fixed Sized Inplace Contiguous Array) (Sequence)

An `array` in C++ stores a fixed number of items. The number of items is decided when you create it, and it cannot change.

### Header
```cpp
#include <array>
```

### Example of Array Initialization
```cpp
std::array<int, 3> numbers = {10, 20, 30}; // This is called aggregate initialization.
```

### Important Notes:
- The size of the array never changes.
- Do not use `front()` or `back()` if the array is empty.
- Swapping two arrays will take linear time.

### If You Create an Empty Array:
```cpp
std::array<int, 0> emptyArray;
```

- `emptyArray.begin() == emptyArray.end()` — they point to the same place.
- But calling `front()` or `back()` on an empty array is undefined behavior (could crash).

### Iterators:
An iterator is like a pointer used to walk through an array.

👉 With `std::array`, iterators remain valid as long as the array exists — you don’t need to worry about them breaking.

🚨 But, if you swap two arrays:
```cpp
std::array<int, 3> a = {1, 2, 3};
std::array<int, 3> b = {4, 5, 6};
std::swap(a, b);
```
An iterator that used to point to an element in `a` will now point to the same position, but the value will have changed, because the arrays have been swapped.

### Template Parameters:
When you write `std::array<int, 5>`, you're using template parameters:
- **T** – the type of elements (e.g., `int`, `float`, `std::string`). Must support moving (copying without duplicating data).
- **N** – the number of elements in the array. This can be any number, even 0.

### Iterators Types:
There are several types of iterators:
- **Normal Iterators**:
  - `iterator` – lets you move from start to end.
  - `const_iterator` – same as above, but you can’t change the values.
  
- **Reverse Iterators**:
  - `reverse_iterator` – goes from end to start.
  - `const_reverse_iterator` – same, but read-only.

These are automatically created:
- **Constructor** – creates the array.
- **Destructor** – destroys elements when the array is deleted.
- **Assignment operator** – lets you assign one array to another.

### Functions:
| Function                 | Meaning                          |
| ------------------------ | -------------------------------- |
| `begin()` / `cbegin()`    | Start of array (iterator)        |
| `end()` / `cend()`        | End of array (past last element) |
| `rbegin()` / `crbegin()`  | Start from end (reverse)         |
| `rend()` / `crend()`      | Reverse end (before first)       |

| Function     | Meaning                                                        |
| ------------ | -------------------------------------------------------------- |
| `empty()`    | Is the array empty?                                            |
| `size()`     | How many elements?                                             |
| `max_size()` | Maximum number of elements it can have (same as `size()` here) |

| Function     | What it does                                |
| ------------ | ------------------------------------------- |
| `at(index)`  | Returns element at index, with safety check |
| `operator[]` | Returns element (no check)                  |
| `front()`    | First element                               |
| `back()`     | Last element                                |
| `data()`     | Pointer to the array’s raw data             |

### Example Code:
```cpp
#include <array>
#include<iostream>
using namespace std;

int main() {
   array<int, 3> numbers = {1, 3, 5};
   int numbersTwo[3] = {1, 3, 5};
  
   cout << numbers.front() << endl; // We can access this using front
  
   // cout << numbersTwo.front() << endl; // We cannot access this

   return 0;
}
```
