[//]: # (### When and How to Use a Destructor)

Destructors are essential when a class manages resources that need to be released or cleaned up when objects of that class are destroyed. They're crucial in scenarios involving dynamically allocated memory, open files, database connections, or any acquired resources that need proper cleanup.

#### When to Use a Destructor

1. **Dynamic Memory Allocation:** If a class allocates memory using `new` keyword, a destructor is necessary to deallocate that memory using `delete`.

2. **File Handling:** When a class opens files, databases, or network connections, a destructor can be used to ensure these resources are properly closed when the object is destroyed.

3. **Resource Management:** For classes managing other resources like locks, handles, or connections, a destructor is important to release these resources upon object destruction.

#### How to Use a Destructor

1. **Release Allocated Memory:** If the class allocates memory using `new`, ensure the destructor deallocates this memory using `delete`.

2. **Close Open Resources:** Release any open resources (files, sockets, database connections) by closing or releasing them in the destructor.

3. **Clean Up Object-Specific State:** Perform any necessary cleanup or state reset operations specific to the object's behavior or requirements.

#### Example

```cpp
#include <iostream>
using namespace std;

class Resource {
private:
    int* data; // Pointer for dynamic memory allocation

public:
    Resource() {
        data = new int[10]; // Allocating memory
        cout << "Resource acquired." << endl;
    }

    ~Resource() {
        delete[] data; // Deallocating memory
        cout << "Resource destroyed." << endl;
    }
};

int main() {
    {
        Resource res; // Creating an object of the Resource class

        // Object res goes out of scope at the end of this block
    } // Destructor is automatically called here for the object res

    return 0;
}
```

In this example, the `Resource` class allocates memory dynamically using `new` in the constructor. The destructor `~Resource()` ensures that the allocated memory (`data`) is properly deallocated using `delete[]` when objects of the class are destroyed.

Always ensure that the destructor handles resource cleanup appropriately, preventing memory leaks or resource leaks when objects go out of scope or are explicitly deleted.
