[//]: # (### Dynamic Arrays)

In C++, dynamic arrays are created using pointers and allocated memory from the heap using operators like `new` and `delete`. Unlike static arrays whose sizes are determined at compile-time, dynamic arrays allow for a flexible size determined during runtime. The C++ Standard Library provides containers like `std::vector` that offer dynamic resizing and ease of use, but dynamic arrays are still used when direct memory control is required.

Here's an example of creating a dynamic array:

```cpp
#include <iostream>

int main() {
    int size;
    std::cout << "Enter the size of the array: ";
    std::cin >> size;

    int* dynamicArray = new int[size]; // Allocating memory for the dynamic array

    // Initializing the array
    for (int i = 0; i < size; ++i) {
        dynamicArray[i] = i * 10;
    }

    // Accessing and printing array elements
    for (int i = 0; i < size; ++i) {
        std::cout << "dynamicArray[" << i << "] = " << dynamicArray[i] << std::endl;
    }

    // Freeing the allocated memory to avoid memory leaks
    delete[] dynamicArray;

    return 0;
}
```

In this example:

- `int* dynamicArray = new int[size];` dynamically allocates memory for an array of integers based on the user-provided `size`.
- The memory allocation is done on the heap, and the pointer `dynamicArray` points to the first element of the dynamically allocated array.
- After using the dynamically allocated memory, it's essential to release it using `delete[] dynamicArray` to prevent memory leaks.

Dynamic arrays offer flexibility but require manual memory management. Incorrect memory handling, such as forgetting to deallocate memory using `delete[]` or accessing memory out of bounds, can lead to memory leaks or undefined behavior. Therefore, consider using safer alternatives like `std::vector` for most use cases, as they handle memory management automatically and provide dynamic resizing capabilities.
