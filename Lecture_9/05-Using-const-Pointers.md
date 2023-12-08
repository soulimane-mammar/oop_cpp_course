[//]: # (### Using the const Keyword on Pointers)

The `const` keyword in C++ can be used in various ways with pointers to enforce immutability and prevent unintended modifications to either the pointer itself or the data it points to.

#### 1. `const` with Pointer Declarations

- `const` can be placed to the left of the asterisk (*) to create a constant pointer that cannot be reassigned to point to another memory location:

    ```cpp
    int x = 10;
    int y = 20;

    int* const ptr = &x; // Constant pointer to an integer
    *ptr = 30; // Valid - can modify the value at the memory location
    // ptr = &y; // Invalid - cannot reassign ptr to point elsewhere
    ```

#### 2. `const` Pointers to Constant Data

- `const` can be placed to the right of the asterisk (*) to create a pointer to constant data. This prevents modification of the data the pointer is pointing to:

    ```cpp
    int x = 10;
    const int* ptr = &x; // Pointer to constant integer

    // *ptr = 20; // Invalid - cannot modify the value through ptr
    x = 20; // Valid - x can be modified directly

    const int y = 30;
    ptr = &y; // Valid - pointer can point to another constant integer
    ```

#### 3. `const` Pointers to Constant Data (Const-correctness)

- To create a pointer that cannot modify the data and cannot be reassigned to point elsewhere, combine both types of `const`:

    ```cpp
    int x = 10;
    const int* const ptr = &x; // Constant pointer to constant integer

    // *ptr = 20; // Invalid - cannot modify the value through ptr
    // ptr = &y; // Invalid - cannot reassign ptr to point elsewhere
    ```
