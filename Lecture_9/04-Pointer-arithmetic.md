[//]: # (#### Pointer Arithmetic)

Pointer arithmetic involves performing arithmetic operations on pointers in C++ to navigate through memory locations. This is particularly useful when working with arrays or allocating contiguous memory for data structures.

#### Basic Pointer Arithmetic Operations

1. **Incrementing/Decrementing Pointers:**
   - When you increment a pointer (`ptr++`), it moves to the next memory location of its type.
   - When you decrement a pointer (`ptr--`), it moves to the previous memory location of its type.

    ```cpp
    int arr[] = {1, 2, 3, 4, 5};
    int *ptr = arr; // Pointer pointing to the start of the array

    cout << *ptr << endl; // Output: 1
    ptr++; // Moves to the next memory location
    cout << *ptr << endl; // Output: 2
    ```

2. **Adding/Subtracting Integers to Pointers:**
   - Adding an integer to a pointer advances it by that many elements of its type.
   - Subtracting an integer from a pointer moves it back by that many elements of its type.

    ```cpp
    int arr[] = {1, 2, 3, 4, 5};
    int *ptr = arr;

    cout << *ptr << endl; // Output: 1
    ptr = ptr + 2; // Moves two elements ahead
    cout << *ptr << endl; // Output: 3
    ```

3. **Subtracting Pointers:**
   - Subtracting one pointer from another gives the difference in elements of their type.

    ```cpp
    int arr[] = {1, 2, 3, 4, 5};
    int *ptr1 = &arr[2]; // Pointer pointing to the third element
    int *ptr2 = &arr[0]; // Pointer pointing to the first element

    cout << ptr1 - ptr2 << endl; // Output: 2 (difference in elements)
    ```

#### Precautions

- Pointer arithmetic should be used with caution to ensure that pointers do not point outside the allocated memory. Operating beyond the boundaries of allocated memory can lead to undefined behavior and bugs like segmentation faults.
- It's crucial to understand the size of the data type being pointed to, especially when performing arithmetic operations on pointers.
