[//]: # (### C++ Syntax of Derivation)

In C++, the syntax for deriving a class from a base class involves using the `class` keyword followed by a colon (`:`) and the access specifier along with the name of the base class.

Here's the basic syntax:

```cpp
// Base class
class BaseClass {
    // Base class members
};

// Derived class inheriting from BaseClass
class DerivedClass : access_specifier BaseClass {
    // Additional members or modifications
};
```

Explanation:

- `class BaseClass` defines the base class.
- `class DerivedClass : access_specifier BaseClass` signifies the creation of a derived class named `DerivedClass` that inherits from `BaseClass`.
- `access_specifier` can be one of the access specifiers: `public`, `protected`, or `private`, indicating the access level for the inherited members in the derived class.

For example:

```cpp
#include <iostream>
using namespace std; 

class Fish
{
public:
   bool isFreshWaterFish;

   void Swim()
   {
      if (isFreshWaterFish)
         cout << "Swims in lake" << endl;
      else
         cout << "Swims in sea" << endl;
   }
};

class Tuna: public Fish
{
public:
   Tuna()
   {
      isFreshWaterFish = false;
   }
};

class Carp: public Fish
{
public:
   Carp()
   {
      isFreshWaterFish = true;
   }
};

int main()
{
   Carp myLunch;
   Tuna myDinner;

   cout << "About my food" << endl;

   cout << "Lunch: ";
   myLunch.Swim();

   cout << "Dinner: ";
   myDinner.Swim();

   return 0;
}
```

Output

```
About my food: 
Lunch: Swims in lake 
Dinner: Swims in sea
```

In the `main()` function, instances of the classes `Carp` and `Tuna` are created, named `myLunch` and `myDinner`, respectively. We proceed to prompt these instances to swim by calling the `Swim()` method. The class definitions for `Tuna` and `Carp` are succinct, with their constructors adjusting the Boolean flag `Fish::isFreshWaterFish` within the base class to appropriate values. This flag is later referenced within the `Fish::Swim()` function. Notably, neither of the derived classes explicitly defines the `Swim()` method that we successfully invoked in `main()`. This accessibility is due to `Swim()` being a public member of the base class `Fish`, inherited by instances of the derived classes `Carp` and `Tuna` through public inheritance. This inheritance exposes the base class's public members to the derived classes.
