[//]: # (### Class That Does Not Permit Copying)

To create a class that does not allow copying, you can delete the copy constructor and the copy assignment operator. This prevents instances of the class from being copied, enforcing unique ownership or prohibiting the creation of duplicate objects.

#### Example of a Non-Copyable Class

```cpp
#include <iostream>
#include <cstring>
using namespace std;

class NonCopyable {
private:
    char* data;

public:
    // Constructor
    NonCopyable(const char* str) {
        int length = strlen(str) + 1;
        data = new char[length];
        strcpy(data, str);
    }

    // Delete the copy constructor to prevent copying
    NonCopyable(const NonCopyable& other) = delete;

    // Delete the copy assignment operator to prevent assignment
    NonCopyable& operator=(const NonCopyable& other) = delete;

    // Display method
    void displayData() {
        cout << "Data: " << data << endl;
    }

    // Destructor
    ~NonCopyable() {
        delete[] data;
    }
};

int main() {
    NonCopyable obj1("Unique data"); // Creating an object

    // Attempting to create another object using the copy constructor or copy assignment
    // NonCopyable obj2 = obj1; // Error: Attempted to use deleted function
    // NonCopyable obj3(obj1); // Error: Attempted to use deleted function

    obj1.displayData(); // Output: Data: Unique data

    return 0;
}
```

In this example:

- The `NonCopyable` class defines a copy constructor and copy assignment operator as `delete`, which means they cannot be used to copy objects of this class.
- Attempting to create another object by copying `obj1` using the copy constructor or copy assignment operator results in a compilation error due to the deleted functions.
- This prevents accidental copying of instances of the `NonCopyable` class, ensuring unique ownership of resources managed by objects of this class.

This technique is particularly useful for classes managing exclusive resources, preventing unintentional sharing or copying of those resources and enforcing the notion of unique ownership.
