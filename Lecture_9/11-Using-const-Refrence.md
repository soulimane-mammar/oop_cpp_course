
[//]: #  (### Using the Keyword const on References)

Using the `const` keyword with references in C++ allows you to create references that promise not to modify the referenced variable. It ensures that the referenced variable cannot be modified through that particular reference.

#### Syntax for Creating Const References

The syntax for creating a `const` reference involves placing the `const` keyword before the reference declaration:

```cpp
int value = 10;
const int &constRef = value; // Const reference to an integer variable
```

#### Characteristics of Const References

1. **Read-only Access:** A `const` reference guarantees read-only access to the referenced variable. Attempting to modify the variable through a `const` reference results in a compilation error.

2. **Preventing Modifications:** It serves as a promise to not modify the referenced variable through that specific reference.

#### Example Usage

```cpp
#include <iostream>
using namespace std;

int main() {
    int number = 5;
    const int &constRef = number; // Const reference to an integer

    cout << "Value: " << number << endl;      // Output: Value: 5
    cout << "Const reference: " << constRef << endl; // Output: Const reference: 5

    // Attempting to modify through a const reference (results in a compilation error)
    // constRef = 10;

    return 0;
}
```

In this example, `constRef` is a `const` reference to the `number` variable. Any attempt to modify `number` through `constRef` will result in a compilation error because `constRef` guarantees read-only access to `number`.

Using `const` references is beneficial when you want to ensure that a referenced variable is not modified accidentally or when you want to pass variables to functions with the assurance that they won't be changed within the function. It's a useful way to enhance code safety and express the intent of not modifying specific variables through certain references.
