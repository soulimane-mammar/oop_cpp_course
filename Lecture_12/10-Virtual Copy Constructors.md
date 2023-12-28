[//]: # (### Virtual Copy Constructors?)

It is technically impossible in C++ to have virtual copy constructors.

However, such a feature would help you create a collection (for example, a static array) of type `Base*`, with each element being a specialization of that type:

```cpp
// Tuna, Carp and Trout are classes that inherit public from base class Fish 
Fish* pFishes[3]; 
Fishes[0] = new Tuna(); 
Fishes[1] = new Carp();
Fishes[2] = new Trout();
```

Then assigning it into another array of the same type, where the virtual copy constructor ensures a deep copy of the derived class objects as well, ensures that `Tuna`, `Carp`, and `Trout` are copied properly even though the copy constructor is operating on the type Fish*.

**Well, that's not possible**

Constructors are responsible for initializing objects and are called during object creation, and they cannot be inherited or overridden like regular member functions.

Having said that, there is a nice workaround in the form of defining your own clone function that allows you to do just that:

```cpp
#include <iostream>
using namespace std;

class Fish
{
public:
   virtual Fish* Clone() = 0;
   virtual void Swim() = 0;
   virtual ~Fish() {};
};

class Tuna: public Fish
{
public:
   Fish* Clone() override
   {
      return new Tuna (*this);
   }

   void Swim() override final
   {
      cout << "Tuna swims fast in the sea" << endl;
   }
};

class BluefinTuna final:public Tuna
{
public:
   Fish* Clone() override
   {
      return new BluefinTuna(*this);
   }

   // Cannot override Tuna::Swim as it is "final" in Tuna
};

class Carp final: public Fish
{
   Fish* Clone() override
   {
      return new Carp(*this);
   }
   void Swim() override final
   {
      cout << "Carp swims slow in the lake" << endl;
   }
};

int main()
{
   const int ARRAY_SIZE = 4;

   Fish* myFishes[ARRAY_SIZE];
   myFishes[0] = new Tuna();
   myFishes[1] = new Carp();
   myFishes[2] = new BluefinTuna();
   myFishes[3] = new Carp();

   Fish* myNewFishes[ARRAY_SIZE];
   for (int index = 0; index < ARRAY_SIZE; ++index)
      myNewFishes[index] = myFishes[index]->Clone();

   // invoke a virtual method to check
   for (int index = 0; index < ARRAY_SIZE; ++index)
      myNewFishes[index]->Swim();

   // memory cleanup
   for (int index = 0; index < ARRAY_SIZE; ++index)
   {
      delete myFishes[index];
      delete myNewFishes[index];
   }

   return 0;
}
```

Output

```
Tuna swims fast in the sea 
Carp swims slow in the lake 
Tuna swims fast in the sea 
Carp swims slow in the lake
```

Note how the array `myFishes` is able to collect seemingly different types that are all related by a common base type `Fish`. We were also able to copy into a new array of type Fish* called `myNewFishes` by using the virtual function `Fish::Clone()` within a loop.
