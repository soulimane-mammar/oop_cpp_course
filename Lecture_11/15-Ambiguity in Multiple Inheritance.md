[//]: # (### Ambiguity in Multiple Inheritance)

Multiple inheritance can lead to ambiguity when a derived class inherits from multiple base classes that share common member names or functions. This ambiguity arises due to the compiler being uncertain about which inherited member to use in certain contexts.

Here's an example illustrating the ambiguity:

```cpp
#include <iostream>
using namespace std;

class Base1 {
public:
    void display() {
        cout << "Display from Base1" << endl;
    }
};

class Base2 {
public:
    void display() {
        cout << "Display from Base2" << endl;
    }
};

class Derived : public Base1, public Base2 {
public:
    // ...
};

int main() {
    Derived derivedObj;
    // derivedObj.display();  // Error: Ambiguous call to 'display'
    return 0;
}
```

In this scenario, `Derived` class inherits `display()` functions from both `Base1` and `Base2`. When trying to call `display()` on `derivedObj`, it leads to a compilation error due to ambiguity (`error: request for member 'display' is ambiguous`).

To resolve this ambiguity, you can explicitly specify which `display()` function to use by employing the scope resolution operator:

```cpp
int main() {
    Derived derivedObj;
    derivedObj.Base1::display(); // Calls display() from Base1
    derivedObj.Base2::display(); // Calls display() from Base2
    return 0;
}
```

Using the scope resolution operator (`Base1::display()` or `Base2::display()`) clarifies which inherited member function to invoke, resolving the ambiguity.

To avoid such complexities, it's recommended to prevent naming conflicts or reconsider the design if multiple inheritance leads to ambiguities. Virtual inheritance is another technique that can be used to resolve ambiguities in more complex cases, ensuring only a single instance of shared base class members in the most derived class.
