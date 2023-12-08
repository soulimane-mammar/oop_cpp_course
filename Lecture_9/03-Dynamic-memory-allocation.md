[//]: # (### Dynamic Memory Allocation)

Dynamic memory allocation in C++ refers to the process of allocating memory at runtime rather than compile time. This flexibility is beneficial when the size of data needed is unknown at compile time or when the data size needs to change during program execution. This is done using operators like `new` and `delete`.

#### `new` Operator

The `new` operator is used to allocate memory for a single variable or an array dynamically. For example:

```cpp
int *ptr = new int; // Allocates memory for a single integer
int *arr = new int[10]; // Allocates memory for an array of 10 integers
```

#### `delete` Operator

The `delete` operator deallocates memory that was allocated using `new`. For single variables:

```cpp
delete ptr; // Deallocates memory for a single integer
```

For arrays:

```cpp
delete[] arr; // Deallocates memory for the array of integers
```

#### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int *ptr = new int; // Allocating memory for a single integer
    *ptr = 10; // Assigning a value to the allocated memory

    cout << "Value pointed by ptr: " << *ptr << endl;

    delete ptr; // Deallocating memory to avoid memory leaks

    return 0;
}
```

#### Memory Management Best Practices

1. Always deallocate memory allocated using `new` with `delete`.
2. When using `new[]` to allocate arrays, use `delete[]` to deallocate the memory.
3. Failure to deallocate memory can lead to memory leaks, where memory is allocated but not released, causing your program to consume more and more memory over time.

However, modern C++ encourages the use of smart pointers (`std::unique_ptr`, `std::shared_ptr`, etc.) and containers (`std::vector`, `std::array`) as they help manage memory automatically, reducing the risk of memory leaks and making code cleaner and safer.
