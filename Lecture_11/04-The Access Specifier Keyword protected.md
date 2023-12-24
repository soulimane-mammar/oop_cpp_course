[//]: # (### The Access Specifier Keyword protected)

In the previous example, the class `Fish` features a public attribute named `isFreshWaterFish`, which is customized by the derived classes `Tuna` and `Carp` to tailor the behavior of `Fish` for saltwater and freshwater, respectively. However, a significant issue arises within the program: the public nature of `Fish::isFreshWaterFish` permits even the `main()` function to manipulate this Boolean flag externally, potentially leading to unintended alterations, such as `myDinner.isFreshWaterFish = true; // despite Tuna not being a freshwater fish!` Clearly, there's a necessity for a mechanism granting access to derived class members for modifying specific attributes of the base class while preventing external access. This indicates a requirement for `isFreshWaterFish` in the `Fish` class to be accessible exclusively to `Tuna` and `Carp` classes, but not to `main()`. This is precisely where the keyword `protected` comes into play.

```cpp
#include <iostream>
using namespace std; 

class Fish
{
protected:
   bool isFreshWaterFish; // accessible only to derived classes

public:
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
      isFreshWaterFish = false; // set base class protected member
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

   // uncomment line below to see that protected members
   // are not accessible from outside the class heirarchy
   // myLunch.isFreshWaterFish = false;

   return 0;
}
```

Output

```
About my food: 
Lunch: Swims in lake 
Dinner: Swims in sea
```

Although the output of the preceding example matches that of this one, several significant modifications have been made to the `Fish` class. The primary and crucial alteration is the transformation of the Boolean member `Fish::isFreshWaterFish` into a protected attribute, making it inaccessible through `main()`. If the line `myLunch.isFreshWaterFish = false;` is uncommented, a compiler error will result. Nevertheless, this member of the `Fish` class, defined with the access specifier `protected`, remains accessible within the derived classes `Tuna` and `Carp`.
