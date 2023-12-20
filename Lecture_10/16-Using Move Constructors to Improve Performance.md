[//]: # (### Using Move Constructors to Improve Performance)

Move constructors in C++ enable the efficient transfer of resources (like dynamically allocated memory or unique ownership) from one object to another, reducing unnecessary copying overhead. They are used to transfer the internal resources of an object to a new object, leaving the source object in a valid but unspecified state.

#### Move Constructors vs. Copy Constructors

- **Copy Constructor:** Performs a deep copy of resources, creating a new copy of the data owned by the source object.
  
- **Move Constructor:** Transfers ownership of resources, efficiently moving the data from the source object to the destination object, typically leaving the source in a state where it's valid but not guaranteed.

#### Example Demonstrating Move Constructor Usage

```cpp
#include <iostream>
#include <cstring>
using namespace std;

class StringWrapper {
private:
    char* str;

public:
    // Constructor
    StringWrapper(const char* s) {
        int length = strlen(s) + 1;
        str = new char[length];
        strcpy(str, s);
    }

    // Move constructor
    StringWrapper(StringWrapper&& other) noexcept : str(other.str) {
        other.str = nullptr; // Nullify the source pointer to avoid double deletion
    }

    // Display method
    void displayString() {
        if (str) {
            cout << "String: " << str << endl;
        } else {
            cout << "String is null" << endl;
        }
    }

    // Destructor
    ~StringWrapper() {
        delete[] str;
    }
};

int main() {
    StringWrapper original("Move me"); // Creating an original object
    original.displayString(); // Output: String: Move me

    StringWrapper moved = std::move(original); // Using move constructor
    original.displayString(); // Output: String is null
    moved.displayString(); // Output: String: Move me

    return 0;
}
```

In this example:

- The `StringWrapper` class has a move constructor `StringWrapper(StringWrapper&& other)` defined using the double ampersand (`&&`) syntax to denote an rvalue reference.
- `std::move()` is used to cast `original` to an rvalue, allowing the move constructor to transfer ownership of the `str` pointer from `original` to `moved`.
- After moving the resources, `original` is left in a valid but unspecified state, with its `str` pointer set to `nullptr`.
