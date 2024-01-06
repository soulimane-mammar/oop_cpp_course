[//]: # (### Using dynamic_cast and Runtime Type Identification)

`dynamic_cast` is a special casting operator in C++ that is primarily used for performing safe downcasting at runtime. It is part of the RTTI (Run-Time Type Information) mechanism in C++. The `dynamic_cast` operator is used to convert pointers or references of a base class to a derived class, a process known as downcasting.
Here is a simple example of `dynamic_cast`:

```cpp
class Base {
public:
   virtual void print() {
       cout << "Base" << endl;
   }
};

class Derived : public Base {
public:
   void print() override {
       cout << "Derived" << endl;
   }
};

int main() {
   Base* bp = new Derived();
   Derived* dp = dynamic_cast<Derived*>(bp);

   if (dp != nullptr) {
       cout << "Successful downcasting" << endl;
   } else {
       cout << "Failed downcasting" << endl;
   }

   delete bp;
   return 0;
}
```

In this example, a `Base` pointer (`bp`) is pointing to a `Derived` object. We then attempt to downcast this `Base` pointer to a `Derived` pointer using `dynamic_cast`. If the cast is successful, `dynamic_cast` will return a valid pointer to the `Derived` object. Otherwise, it will return a null pointer [Source 1](https://www.geeksforgeeks.org/dynamic-_cast-in-cpp/).

`dynamic_cast` has several key characteristics:

- It can be used for both upcasting (converting from a derived class to a base class) and downcasting (converting from a base class to a derived class).
- It checks whether the cast is safe at runtime. If the cast is not safe (i.e., the object being pointed to is not actually an instance of the target class), `dynamic_cast` will return a null pointer.
- It requires the base class to have at least one virtual function to enable the RTTI mechanism.

In situations where you need to determine the exact type of a derived class object through a base class pointer, `dynamic_cast` is often the preferred tool.
