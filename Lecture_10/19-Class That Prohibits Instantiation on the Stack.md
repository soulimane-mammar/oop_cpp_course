[//]: # (### Class That Prohibits Instantiation on the Stack)

To create a class that prohibits instantiation on the stack, you can achieve this by making the class constructor private and providing a static function that returns an instance of the class created on the heap using the `new` keyword. This approach ensures that objects of the class cannot be instantiated directly on the stack but only through the provided static function.

#### Example of a Class Prohibiting Stack Instantiation

```cpp
#include <iostream>
using namespace std;

class NoStackInstantiation {
private:
    // Private constructor to prevent stack instantiation
    NoStackInstantiation() {}

public:
    // Static function to get an instance of the class
    static NoStackInstantiation* getInstance() {
        return new NoStackInstantiation();
    }

    // Method to demonstrate the class instance
    void showMessage() {
        cout << "Instance created!" << endl;
    }

    // Destructor to release the heap-allocated memory
    ~NoStackInstantiation() {
        cout << "Instance destroyed!" << endl;
    }
};

int main() {
    // Attempting to instantiate the class on the stack
    // NoStackInstantiation obj; // Error: Cannot access constructor

    // Accessing the class instance through the static function
    NoStackInstantiation* objPtr = NoStackInstantiation::getInstance();
    objPtr->showMessage(); // Output: Instance created!

    // Deleting the heap-allocated instance
    delete objPtr; // Output: Instance destroyed!

    return 0;
}
```

In this example:

- The `NoStackInstantiation` class has a private constructor, preventing direct instantiation on the stack.
- The `getInstance()` method returns an instance of the class created on the heap using `new`.
- Attempting to create an object of this class on the stack results in a compilation error due to the private constructor.
- Accessing the class instance is only possible through the `getInstance()` method, ensuring instances are created on the heap.

By restricting instantiation to the heap, you can control the creation and destruction of objects and prevent accidental stack-based instantiation, ensuring the object's lifecycle is managed explicitly through heap allocation and deallocation.
