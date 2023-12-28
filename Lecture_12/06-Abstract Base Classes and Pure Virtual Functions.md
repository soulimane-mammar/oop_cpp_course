[//]: # (### Abstract Base Classes and Pure Virtual Functions)

Pure virtual functions are functions declared in a base class that have no implementation and are meant to be overridden by derived classes. They are defined using the syntax:

```cpp
virtual void functionName() = 0;
```

Here's an example:

```cpp
class Base {
public:
    // Pure virtual function
    virtual void function() = 0;

    // Normal member function
    void normalFunction() {
        // Some implementation
    }
};
```

In this example:

- `function()` is a pure virtual function declared in the `Base` class by appending `= 0`.
- Classes inheriting from `Base` must override `function()` to become concrete classes.
- `normalFunction()` is a regular member function with an implementation and doesn't need to be overridden in derived classes.
- Attempting to instantiate an object of `Base` will result in a compilation error due to the existence of the pure virtual function.

An abstract class is a class that typically contains one or more pure virtual functions and cannot be instantiated on its own. It's designed to serve as a base for other classes to inherit from and provide implementations for its pure virtual functions. Abstract classes are used to define interfaces or common behaviors shared among multiple derived classes.

Here's an example illustrating an abstract class:

```cpp
#include <iostream>
using namespace std;

class Fish
{
public:
   // define a pure virtual function Swim
   virtual void Swim() = 0;
};

class Tuna:public Fish
{
public:
   void Swim()
   {
      cout << "Tuna swims fast in the sea!" << endl;
   }
};

class Carp:public Fish
{
   void Swim()
   {
      cout << "Carp swims slow in the lake!" << endl;
   }
};

void MakeFishSwim(Fish& inputFish)
{
   inputFish.Swim();
}

int main()
{
   // Fish myFish;   // Fails, cannot instantiate an ABC
   Carp myLunch;
   Tuna myDinner;

   MakeFishSwim(myLunch);
   MakeFishSwim(myDinner);

   return 0;
}

```

Output

```
Carp swims slow in the lake! 
Tuna swims fast in the sea!
```

The first line in `main()` (which is commented out), is significant. It demonstrates that the compiler does not allow you to create an instance of an abstract base class `Fish`. It expects something concrete, such as a specialization of `Fish` (for example, `Tuna`).

Thanks to the pure virtual function `Fish::Swim()` , both `Tuna` and `Carp` are forced into implementing `Tuna::Swim()` and `Carp::Swim()`.  

`MakeFishSwim(Fish&)`, demonstrate that even if an abstract base class cannot be instantiated, you can use it as a reference or a pointer.
