[//]: # (### A Derived Class Hiding the Base Class’s Methods)

Overriding can reach an extreme level where `Tuna::Swim()` might hide all the overloaded versions of `Fish::Swim()`, leading to potential compilation failures when attempting to use the overloaded versions. This extreme form of overriding is referred to as "hidden". You can observe an example of this in  the following code

```cpp
#include <iostream>
using namespace std; 
   
class Fish
{
public:
   void Swim()
   {
    cout << "Fish swims... !" << endl;
   }

   void Swim(bool isFreshWaterFish)
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
   void Swim()
   {
      cout << "Tuna swims real fast" << endl;
   }
};

int main()
{
   Tuna myDinner;

   cout << "About my food" << endl;

   //uncomment line below to see failure because Tuna::Swim() hides Fish::Swim(bool)
   // myDinner.Swim(false);

   myDinner.Swim();

   return 0;
}
```

Output

```
About my food 
Tuna swims real fast
```

This version of the class `Fish` is a bit different from the versions we have seen so far. This version of Fish contains two overloaded methods for `Swim()`: one that takes no parameters, and another that takes a bool parameter. As `Tuna` inherits public from Fish, we would not be wrong to expect that both versions of the method `Fish::Swim()` would be available via an instance of the class Tuna. The fact is, however, that `Tuna` implementing its own `Tuna::Swim()`, results in the hiding of `Fish::Swim(bool)` from the compiler.

So, if we want to invoke the `Fish::Swim(bool)` function via an instance of `Tuna`, you can use any of the following solutions:

- **Solution 1:** Use the scope resolution operator in `main()`:

  ```cpp
  myDinner.Fish::Swim();
  ```

- **Solution 2:** Use the keyword `using`in the class `Tuna` to unhide `Swim()` in the class `Fish`:

  ```cpp
  class Tuna: public Fish { 
  public: 
    using Fish::Swim; // unhide all Swim() methods in class Fish 
    void Swim() { 
        cout << “Tuna swims real fast” << endl; 
    } 
  };
  ```

- **Solution 3:** Override all overloaded variants of `Swim()` in the class `Tuna` (such as by invoking methods of `Fish::Swim(...)` via `Tuna::Fish(...)`):

  ```cpp
  class Tuna: public Fish { 
  public: 
    void Swim(bool isFreshWaterFish) { 
            Fish::Swim(isFreshWaterFish); 
    } 
    void Swim() { 
        cout << “Tuna swims real fast” << endl;
    }    
  };  
  ```
