[//]: # (### Base Class Initialization)

If a base class has multiple constructors requiring arguments during instantiation, handling its instantiation within a derived class involves employing initialization lists. This enables the derived class constructor to select and invoke the suitable base class constructor. Here's an example demonstrating this concept:

```cpp
class BaseClass {
public:
    BaseClass(int arg1) {
        // Constructor expecting an argument
    }

    BaseClass(int arg1, int arg2) {
        // Overloaded constructor expecting different arguments
    }
};

class DerivedClass : public BaseClass {
public:
    // Derived class constructor invoking the appropriate base class constructor
    DerivedClass(int derivedArg1, int derivedArg2) : BaseClass(derivedArg1, derivedArg2) {
        // Body of the derived class constructor
    }
};
```

In this setup, the `DerivedClass` constructor employs an initialization list to call the relevant `BaseClass` constructor. It passes arguments `derivedArg1` and `derivedArg2` that correspond to the appropriate base class constructor, allowing the derived class to instantiate the base class with the necessary arguments during its own construction.

This mechanism can be quite useful in the class `Fish`, where, by supplying a Boolean input parameter to the constructor of `Fish` that initializes `Fish::isFreshWaterFish`, this base class `Fish` can ensure that every derived class is forced to mention whether a fish is a freshwater one or a saltwater one, as shown in the following code

```cpp
#include <iostream>
using namespace std; 

class Fish
{
protected:
   bool isFreshWaterFish; // accessible only to derived classes

public:
   // Fish constructor
   Fish(bool isFreshWater) : isFreshWaterFish(isFreshWater){}

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
   Tuna(): Fish(false) {}
};

class Carp: public Fish
{
public:
   Carp(): Fish(true) {}
};

int main()
{
   Carp myLunch;
   Tuna myDinner;

   cout << "Getting my food to swim" << endl;

   cout << "Lunch: ";
   myLunch.Swim();

   cout << "Dinner: ";
   myDinner.Swim();

   return 0;
}
```
