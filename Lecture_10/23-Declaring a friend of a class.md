[//]: # (### Declaring a friend of a class)

In C++, the `friend` keyword is used to grant access to private and protected members of a class to functions or other classes that are not part of the class hierarchy.

#### Declaring a Function or a Class as a Friend

```cpp
#include <iostream>
using namespace std;

class MyClass {
private:
    int privateVar;

public:
    MyClass() : privateVar(0) {}

    // Declaring the external function as a friend
    friend void externalFunction(MyClass& obj);

    // Declaring AnotherClass as a friend class
    friend class AnotherClass;

    void displayPrivateVar() {
        cout << "Private Variable: " << privateVar << endl;
    }
};

// Definition of the external function that is a friend of MyClass
void externalFunction(MyClass& obj) {
    obj.privateVar = 100; // Accessing private member of MyClass
}

class AnotherClass {
public:
    void modifyPrivateVar(MyClass& obj, int value) {
        obj.privateVar = value; // Accessing private member of MyClass
    }
};


int main() {
    MyClass obj;
    externalFunction(obj); // Calls the friend function
    obj.displayPrivateVar(); // Output: Private Variable: 100

    AnotherClass friendObj;

    friendObj.modifyPrivateVar(obj, 200); // Modify private member of MyClass
    obj.displayPrivateVar(); // Output: Private Variable: 200

    return 0;
}
```

Explanation:

- `MyClass` declares `externalFunction` and `AnotherClass` as a friends using the `friend` keyword.
- The `externalFunction` is defined outside the class and can access the private member `privateVar` of `MyClass`.
- Inside `externalFunction`, it directly accesses and modifies the private member of `MyClass`.
- Similarly `AnotherClass` now has access to the private member privateVar of MyClass. Inside the `modifyPrivateVar()` function of `AnotherClass`, it directly modifies the private member `privateVar` of `MyClass`.

Remember that while `friend` functions or classes can access the private members of the class, excessive use of the `friend` keyword can break encapsulation, making the code less maintainable and harder to debug. Therefore, it's generally recommended to use `friend` sparingly and prefer encapsulation whenever possible.
