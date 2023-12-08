[//]: #  (###Checking Whether an Allocation Request Using new Succeeded)

When using `new` to allocate memory dynamically in C++, it's important to check whether the allocation was successful. If the allocation fails due to insufficient memory or other reasons, `new` might return a `nullptr`.

Here's an example illustrating how to check if an allocation request using `new` succeeded:

```cpp
#include <iostream>
using namespace std;

int main() {
    int* ptr = new (nothrow) int[100]; // Attempting to allocate memory for an array of 100 integers

    if (ptr == nullptr) {
        cout << "Memory allocation failed." << endl;
    } else {
        cout << "Memory allocation successful." << endl;
        // Use the allocated memory here
        delete[] ptr; // Remember to deallocate the memory when done
    }

    return 0;
}
```

In this example:

- `new (nothrow) int[100];` attempts to allocate memory for an array of 100 integers. The `nothrow` specifier ensures that if the allocation fails, `new` returns a `nullptr` instead of throwing an exception.
- The `if` statement checks if the allocation succeeded by verifying if `ptr` is equal to `nullptr`.
- If `ptr` is not `nullptr`, the memory allocation is considered successful, and you can use the allocated memory. Remember to deallocate it using `delete[] ptr;` when you're finished.

It's crucial to check for allocation success, especially in scenarios where memory allocation failures could occur due to limited memory resources. Handling allocation failures gracefully helps prevent crashes or unexpected behavior in your program.
