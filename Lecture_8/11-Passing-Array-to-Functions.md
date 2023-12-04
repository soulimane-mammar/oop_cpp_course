[//]: # (###Passing an Array of Values to a Function)

In C++, when passing an array to a function, you typically need to pass either a pointer to the array or use a reference to an array. Unlike some other languages, arrays decay into pointers when passed to functions, losing information about their size. Here are a couple of approaches:

#### Using Pointers

```cpp
#include <iostream>

// Function that takes an array and its size as parameters
void processArray(int arr[], int size) {
    for (int i = 0; i < size; ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;
}

int main() {
    int myArray[] = {1, 2, 3, 4, 5};
    int length = sizeof(myArray) / sizeof(myArray[0]);

    processArray(myArray, length); // Pass the array and its size to the function

    return 0;
}
```

Here, `processArray` takes an array and its size as parameters. Inside `main()`, `myArray` is passed to `processArray` along with its length calculated by `sizeof(myArray) / sizeof(myArray[0])`.

#### Using References

```cpp
#include <iostream>

// Function that takes a reference to an array and its size as parameters
template <size_t N>
void processArray(int (&arr)[N]) {
    for (size_t i = 0; i < N; ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;
}

int main() {
    int myArray[] = {1, 2, 3, 4, 5};

    processArray(myArray); // Pass the array to the function using a reference

    return 0;
}
```

In this version, `processArray` takes a reference to an array and deduces its size using a template argument (`int (&arr)[N]`). When `processArray` is called in `main()`, `myArray` is passed directly.

Templates will be discussed in details in subsequent lectures.

Remember that in both cases, the function doesn't know the size of the array inherently, so it's a good practice to pass the size explicitly or use data structures like `std::array` or `std::vector` if you need dynamic sizes without losing that information.
