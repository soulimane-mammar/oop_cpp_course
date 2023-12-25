[//]: # (### A Derived Class Overriding the Base Class’s Methods)

If the class `Derived` implements the same functions with the same return values and signatures as in the class `Base` from which it inherits, it effectively overrides that method in the class `Base`, as shown in the following code:

```cpp
class Base {

public: 
    void DoSomething() { 
        // implementation code... Does something 
    } 
}; 

class Derived:public Base { 
public: 
    void DoSomething() { 
        // implementation code... Does something else 
    }
};
```

Thus, if the method `DoSomething()` were to be invoked using an instance of `Derived`, it would not invoke the functionality in the class `Base`.

If the classes `Tuna` and `Carp` were to implement their own `Swim()` method that also exists in the base class as `Fish::Swim()`, then a call to `Swim`, as shown in `main()` from the following code would result in the local implementation of `Tuna::Swim()` being invoked, which would essentially override the base class’s `Fish::Swim()` method:

```cpp
#include <iostream>
using namespace std; 

class Fish
{
private:
   bool isFreshWaterFish;

public:
   // Fish constructor
   Fish(bool IsFreshWater) : isFreshWaterFish(IsFreshWater){}

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

   void Swim()
   {
      cout << "Tuna swims real fast" << endl;
   }
};

class Carp: public Fish
{
public:
   Carp(): Fish(true) {}

   void Swim()
   {
      cout << "Carp swims real slow" << endl;
   }
};

int main()
{
   Carp myLunch;
   Tuna myDinner;

   cout << "About my food " << endl;

   cout << "Lunch: ";
   myLunch.Swim();

   cout << "Dinner: ";
   myDinner.Swim();

   return 0;
}
```

Output

```
About my food 
Lunch: Carp swims real slow 
Dinner: Tuna swims real fast
```
