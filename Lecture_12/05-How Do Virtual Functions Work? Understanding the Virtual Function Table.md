[//]: # (### How Do Virtual Functions Work? Understanding the Virtual Function Table)

The function `MakeFishSwim(Fish&)` in the last example ends up invoking the `Carp::Swim()` or `Tuna::Swim()` methods even though the programmer calls `Fish::Swim()` within it. Clearly, all that the compiler knows is that the function `MakeFishSwim()` will be invoked with arguments of type `Fish&`, but the function ends up executing different `Swim()` methods belonging to different derived classes. The selection of the right `Swim()` method is evidently a decision made at runtime, using logic that implements polymorphism, which is supplied by the compiler at compile time.

Virtual functions are implemented using a combination of vtables (virtual function tables) and vpointers (virtual pointers). Here's an overview of how they are typically implemented:

1. **VTables (Virtual Function Tables):**
   - For classes containing at least one virtual function, the compiler creates a VTable.
   - A VTable is a static array of function pointers, where each pointer corresponds to a virtual function in the class.
   - The VTable is specific to each class and contains addresses of the overridden virtual functions for that class.

2. **VPointers (Virtual Pointers):**
   - Each object of a class containing virtual functions includes a hidden vpointer or vptr.
   - The vpointer is a pointer to the VTable associated with the class of the object.
   - This vpointer is added by the compiler and is used to access the correct VTable at runtime.

3. **Function Call Mechanism:**
   - When a virtual function is called on an object, the compiler uses the vpointer of that object to locate the appropriate VTable.
   - The VTable helps determine the correct function to call based on the actual object's class type (dynamic binding).
   - The function call is then resolved dynamically at runtime to the overridden function from the correct derived class.

4. **Example:**
   Consider a class `Base` that declares N virtual functions:

   ```cpp
   class Base 
   { 
    public: 
        virtual void Func1() 
        { 
            // Func1 implementation 
        } 
        virtual void Func2() 
        { 
            // Func2 implementation 
        } 
        
        // .. so on and so forth 
        virtual void FuncN() 
        { 
            // FuncN implementation 
        } 
   };
   
   ```

The class `Derived`, which inherits from `Base`, overrides `Base::Func2()`, exposing the other virtual functions directly from the class `Base`:

```cpp
class Derived: public Base 
{ 
public: 
    virtual void Func1() { 
        // Derived::Func1 overrides Base::Func1() 
    } 
    // no implementation for Func2() 


    virtual void FuncN() { 
        // FuncN implementation 
    } 
};
```

The compiler sees an inheritance hierarchy and understands that `Base` defines certain virtual functions that have been overridden in Derived.

The compiler now creates a table called the virtual function table (`VFT`) for every class that implements a virtual function.

Objects of classes Base and Derived get pointers to VFTs for Base and Derived.

A VFT can be visualized as a static array containing function pointers, each pointing to the virtual function (or override) of interest, as illustrated in the following figure

![VFT](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/Lecture_12/vft.png?raw=true)

the compiler ensures a lookup in the VFT  and ensures that the proper implementation is invoked.

```cpp
void DoSomething(Base& objBase) 
{ 
    objBase.Func1(); // invoke Derived::Func1 
} 

int main() 
{ 
    Derived objDerived; 
    DoSomething(objDerived); 
};
```

In this case, even though `objDerived` is being interpreted via `objBase` as an instance of the class Base, the VFT pointer in this instance is still pointing to the same table created for the class `Derived`. Thus, `Func1()`, which is executed via this VFT, is certainly `Derived::Func1()`.

The proof of existence of a hidden VFT pointer is demonstrated in the following code, which compares the sizes of two identical classes—one that has virtual functions and another that doesn’t.

```cpp
#include <iostream>
using namespace std;

class SimpleClass
{
   int a, b;

public:
   void DoSomething() {}
};

class Base
{
   int a, b;

public:
   virtual void DoSomething() {}
};

int main() 
{
   cout << "sizeof(SimpleClass) = " << sizeof(SimpleClass) << endl;
   cout << "sizeof(Base) = " << sizeof(Base) << endl;

   return 0;
}
```

Output

32-bit compiler output:

```
sizeof(SimpleClass) = 8 
sizeof(Base) = 12
```

64-bit compiler output:

```
sizeof(SimpleClass) = 8 
sizeof(Base) = 16

```
