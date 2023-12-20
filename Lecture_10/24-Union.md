[//]: # (### Unions)

In C++, a `union` is a user-defined data type that allows storing different data types in the same memory location. Unlike structures, where each member has its own memory space, all members of a union share the same memory. The size of a union is determined by the size of its largest member.

Similar to a struct, a union has members that are public by default. Unlike a struct, however, a union cannot be used in an inheritance hierarchy.

#### Syntax of Union

```cpp
#include <iostream>
using namespace std;

union MyUnion {
    int intValue;
    float floatValue;
    char charValue;
};
```

#### Example Usage

```cpp
int main() {
    MyUnion myUnion;

    myUnion.intValue = 10;
    cout << "Integer Value: " << myUnion.intValue << endl;

    myUnion.floatValue = 3.14f;
    cout << "Float Value: " << myUnion.floatValue << endl;

    myUnion.charValue = 'A';
    cout << "Character Value: " << myUnion.charValue << endl;

    return 0;
}
```

In this example:

- The `MyUnion` union can hold an integer (`int`), a floating-point number (`float`), and a character (`char`) in the same memory space.
- Assigning a value to one member of the union changes the content of the shared memory, affecting all other members.
- Accessing one member after assigning a value to another may yield unexpected results, as the same memory location is used for all members.

#### Caveats and Considerations

- Unions are useful for scenarios where different types of data need to be stored in the same memory space, but they require careful handling due to potential data corruption when members are accessed incorrectly.
- Using a union, especially when changing the type of data stored, requires careful management to ensure the correct interpretation of data.
- Unions give you the flexibility to store one among many permissible types. However, they do not stop you from accessing the contents of one type as another. That is, unions do not enforce type safety. C++17 introduced the ability to use a type-safe alternative to union called `std::variant`.
