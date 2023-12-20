[//]: # (### The Keyword struct and Its Differences from class)

In C++, both `struct` and `class` are used to define custom data types, but they have some key differences in their default access specifiers and intended use cases.

#### `struct` in C++

- **Default Access Specifier:** In a `struct`, member variables and member functions are public by default if no access specifier is explicitly specified.
  
- **Historical Usage:** In C, a `struct` was used primarily for holding data and had no support for encapsulation or member functions.

#### `class` in C++

- **Default Access Specifier:** In a `class`, member variables and member functions are private by default if no access specifier is explicitly specified.
  
- **Intended for OOP:** A `class` supports encapsulation, allowing data hiding and abstraction through private member variables and controlled access via public member functions.

#### Example Illustrating the Differences

```cpp
#include <iostream>
using namespace std;

// Example using struct
struct MyStruct {
    int publicVar;    // Public by default
    void display() { // Public by default
        cout << "Value: " << publicVar << endl;
    }
};

// Example using class
class MyClass {
    // Private by default
    int privateVar;  // Private member
public:
    void setPrivateVar(int value) {
        privateVar = value;
    }

    void displayPrivateVar() {
        cout << "Private Value: " << privateVar << endl;
    }
};

int main() {
    MyStruct structObj;
    structObj.publicVar = 10;
    structObj.display(); // Output: Value: 10

    MyClass classObj;
    classObj.setPrivateVar(20);
    classObj.displayPrivateVar(); // Output: Private Value: 20

    return 0;
}
```

In this example:

- `MyStruct` has a member variable and a member function, both of which are public by default.
- `MyClass` has a private member variable and public member functions to set and display its value, showcasing encapsulation.

In modern C++, the use of `struct` and `class` can be somewhat interchangeable, with the primary difference being the default access specifiers. However, `class` is often preferred when implementing object-oriented concepts like encapsulation, while `struct` is commonly used for simple data structures or when backward compatibility with C code is necessary.
