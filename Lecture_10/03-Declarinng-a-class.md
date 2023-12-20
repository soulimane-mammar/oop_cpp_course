[//]: # (### Declaring a class)

Declaring a class in C++ involves defining its structure, member variables, and member functions. Here's an example of how to declare a simple class:

```cpp
// Class declaration
class MyClass {
private:
    int privateVar; // Private member variable

public:
    // Public member function to set privateVar
    void setPrivateVar(int value) {
        privateVar = value;
    }

    // Public member function to get privateVar
    int getPrivateVar() {
        return privateVar;
    }

    // Constructor to initialize privateVar
    MyClass() {
        privateVar = 0; // Initializing privateVar in the constructor
    }
};
```

Let's break down the components of this class declaration:

- **`class MyClass { ... };`**: Defines the class named `MyClass`.
- **`private:`**: Access specifier, members declared after this keyword are private by default.
- **`int privateVar;`**: Private member variable accessible only within the class.
- **`public:`**: Access specifier, members declared after this keyword are public by default.
- **`void setPrivateVar(int value) { ... }`**: Public member function to set the value of `privateVar`.
- **`int getPrivateVar() { ... }`**: Public member function to retrieve the value of `privateVar`.
- **`MyClass() { ... }`**: Constructor, initializes the class's objects.

This class has a private member variable `privateVar`, which can only be accessed or modified through the public member functions `setPrivateVar` and `getPrivateVar`. The constructor `MyClass()` initializes `privateVar` to 0 when an object of `MyClass` is created.

To use this class, you can create objects of `MyClass` and access its member functions:

```cpp
int main() {
    MyClass obj; // Creating an object of MyClass

    obj.setPrivateVar(42); // Setting the value of privateVar
    int value = obj.getPrivateVar(); // Getting the value of privateVar

    cout << "PrivateVar value: " << value << endl; // Output: PrivateVar value: 42

    return 0;
}
```

This demonstrates how to create an object of the `MyClass` class and access its member functions to manipulate its private member variable.
