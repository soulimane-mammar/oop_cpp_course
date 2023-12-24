[//]: # (### Invoking Methods of a Base Class in a Derived Class)

Typically, `Fish::Swim()` would contain a generic implementation of swimming that is applicable to all fish —tuna and carp included. If the specialized implementations in `Tuna:Swim()` and `Carp::Swim()` need to reuse the base class’s generic implementation of `Fish::Swim()`, we use the scope resolution operator (`::`), as shown in the following code:

```cpp
#include <iostream>
using namespace std; 
   
class Fish
{
private:
   bool isFreshWaterFish;

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
      Fish::Swim();
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
   myDinner.Fish::Swim();

   return 0;
}
```

Output

```
About my food 
Lunch: Carp swims real slow 
Swims in lake 
Dinner: Swims in sea
```
