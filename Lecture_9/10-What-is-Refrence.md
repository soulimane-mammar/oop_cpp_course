[//]: # (### What Is a Reference?)

In C++, a reference is an alias or an alternative name for an existing variable. It allows you to create an alternative name that refers to the same memory location as the original variable. References are often used as an alternative to pointers to work with data indirectly.

#### Syntax for Creating References

The syntax for creating a reference uses the `&` symbol:

```cpp
int num = 5;
int &refNum = num; // Reference to the variable 'num'
```

#### Characteristics of References

1. **Alias to a Variable:** Once initialized, a reference becomes an alias for the variable it references. Any changes made through the reference will affect the original variable, and vice versa.

2. **Cannot be Reassigned:** Unlike pointers, references cannot be reassigned to refer to a different variable. Once initialized, a reference remains bound to the original variable throughout its lifetime.

3. **No Memory Overhead:** References don’t occupy additional memory; they are essentially another name for an existing variable.

#### Example Usage

```cpp
#include <iostream>
using namespace std;

int main() {
    int original = 10;
    int &alias = original;

    cout << "Original: " << original << endl; // Output: Original: 10
    cout << "Alias: " << alias << endl;       // Output: Alias: 10

    alias = 20; // Modifying through the reference
    cout << "Original after modification: " << original << endl; // Output: Original after modification: 20

    original = 30; // Modifying the original variable
    cout << "Alias after modification: " << alias << endl; // Output: Alias after modification: 30

    return 0;
}
```

References are commonly used in functions to pass parameters efficiently, to avoid making copies of large objects, and to enable modification of variables within functions. They offer a convenient and safe way to work with variables indirectly, providing a level of abstraction without the complexities of pointers.
