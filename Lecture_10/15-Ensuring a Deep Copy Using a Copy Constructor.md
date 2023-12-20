[//]: # (### Ensuring a Deep Copy Using a Copy Constructor)

Shallow copying occurs when a copy of an object is made, but the copied object simply points to the same memory locations as the original object for its member variables. This can lead to issues when both objects are modifying the same memory space, causing unintended side effects and memory management problems.

#### Example Demonstrating Shallow Copy

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

    // Copy constructor (shallow copy)
    StringWrapper(const StringWrapper& other) : str(other.str) {}

    // Display method
    void displayString() {
        cout << "String: " << str << endl;
    }

    // Destructor
    ~StringWrapper() {
        delete[] str;
    }
};

int main() {
    StringWrapper original("Hello"); // Creating an original object
    original.displayString(); // Output: String: Hello

    StringWrapper copied = original; // Using the copy constructor for shallow copy
    copied.displayString(); // Output: String: Hello

    // Modifying the string in the original object
    original.displayString(); // Output: String: Hello
    strcpy(original.str, "Changed");

    // Displaying the string from the copied object
    copied.displayString(); // Output: String: Changed

    return 0;
}
```

In this example:

- The `StringWrapper` class performs shallow copying in its copy constructor by copying the pointer to the string (`char* str`) instead of creating a new copy of the string.
- When the original object's string is modified (`strcpy(original.str, "Changed");`), the change is reflected in the copied object as well because they both share the same memory location for the string.

Another significant issue with shallow copying arises when objects with shared resources or dynamically allocated memory go out of scope. When objects share the same memory through shallow copying, deallocating that memory in one object's destructor can affect the other object's validity, leading to undefined behavior, crashes, or memory corruption.

#### Example Demonstrating Problems with Shallow Copy and Destructor

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

    // Copy constructor (shallow copy)
    StringWrapper(const StringWrapper& other) : str(other.str) {}

    // Display method
    void displayString() {
        cout << "String: " << str << endl;
    }

    // Destructor
    ~StringWrapper() {
        delete[] str;
    }
};

void useObject(StringWrapper copyObj) {
    copyObj.displayString() ;
} // Destructor called for obj, causing deletion of str

int main() {

    SringWrapper obj("Scope") ;

    useObject(obj); // Copying and destroying an object within a function scope

    // Accessing the memory that was deallocated in the destructor
    // This leads to undefined behavior or crashes
    // obj.displayString(); // Attempting to access invalidated memory causes issues

    return 0;
}
```

In this example:

- The `StringWrapper` class performs shallow copying in its copy constructor by copying the pointer to the string (`char* str`) instead of creating a new copy of the string.
- An object `obj` of `StringWrapper` is copied within the `useObject()` function, and when this object goes out of scope, its destructor is called, which deletes the memory allocated for `str`.
- In `main` if `obj` try to access its `str`, it would result in undefined behavior or crashes because the memory it was pointing to has been deallocated.

Ensuring a deep copy in C++ using a copy constructor is important when a class contains dynamically allocated memory or other resources that need to be duplicated properly. A deep copy ensures that the new object has its own distinct copy of the resources rather than simply copying references to them.

#### Example of Ensuring a Deep Copy

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

    // Copy constructor for deep copy
    StringWrapper(const StringWrapper& other) {
        int length = strlen(other.str) + 1;
        str = new char[length];
        strcpy(str, other.str);
    }

    // Display method
    void displayString() {
        cout << "String: " << str << endl;
    }

    // Destructor
    ~StringWrapper() {
        delete[] str;
    }
};

int main() {
    StringWrapper original("Hello"); // Creating an original object
    original.displayString(); // Output: String: Hello

    StringWrapper copied = original; // Using the copy constructor for a deep copy
    copied.displayString(); // Output: String: Hello

    return 0;
}
```

In this example:

- The `StringWrapper` class contains a dynamically allocated string (`char* str`) in its member variables.
- The copy constructor `StringWrapper(const StringWrapper& other)` is defined to perform a deep copy of the string by allocating new memory and copying the contents from the existing object.
- Proper memory allocation and copying are done in the constructor and the copy constructor to ensure that each object has its own distinct copy of the string.
