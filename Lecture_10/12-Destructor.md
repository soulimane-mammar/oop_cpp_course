[//]: # (### Destructors)

A destructor in C++ is a special member function of a class that is automatically called when an object of that class goes out of scope or is explicitly deleted. Its main purpose is to release resources allocated by the object, perform cleanup operations, or deallocate memory that the object might have acquired during its lifetime.

#### Characteristics of Destructors

1. **Same Name as Class with ~:** Destructors have the same name as the class, preceded by a tilde (`~`). They don't have any parameters and don't return a value.

2. **Automatically Called:** Destructors are automatically invoked when the scope of an object ends or when the `delete` operator is used to deallocate dynamically allocated memory.

3. **Release Resources:** They are used to release resources like memory, close files, release locks, or perform cleanup actions required before the object is destroyed.

4. **Only One Destructor per Class:** A class can have only one destructor, and it cannot have parameters or be overloaded.

### Example of a Destructor

```cpp
#include <iostream>
using namespace std;

class Resource {
public:
    Resource() {
        cout << "Resource acquired." << endl;
    }

    ~Resource() {
        cout << "Resource destroyed or released." << endl;
    }
};

int main() {
    {
        Resource res; // Creating an object of the Resource class

        // Object res goes out of scope at the end of this block
    } // Destructor is automatically called here for the object res

    Resource* ptr = new Resource(); // Creating an object using dynamic memory allocation
    delete ptr; // Destructor is explicitly called when deleting dynamically allocated object

    return 0;
}
```

In this example:

- The `Resource` class has a constructor that prints a message when a resource is acquired and a destructor that prints a message when a resource is destroyed or released.
- Inside `main()`, an object of the `Resource` class is created (`res`). When the object goes out of scope at the end of the block, the destructor is automatically called.
- Another object of `Resource` is created using dynamic memory allocation (`new`). The `delete` operator is used to explicitly call the destructor and deallocate the memory for the object.
