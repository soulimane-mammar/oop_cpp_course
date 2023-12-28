[//]: # (### Basics of Polymorphism)

”Poly” is Greek for many, and “morph” means form. Polymorphism is a feature of object-oriented languages that allows objects of different types to be treated similarly. This lesson focuses on polymorphic behavior that can be implemented in C++ via the inheritance hierarchy, also known as subtype polymorphism.

#### Need for Polymorphic Behavior

In Lesson 10, “Implementing Inheritance,” you found out how `Tuna` and `Carp` inherit the public method `Swim()` from `Fish`. It is, however, possible that both `Tuna` and `Carp` provide their own `Tuna::Swim()` and `Carp::Swim()` methods to make `Tuna` and `Carp` different swimmers.

However, as each of them is also a `Fish`, if a user with an instance of `Tuna` uses the base class type to invoke `Fish::Swim()`, he ends up executing only the generic part `Fish::Swim()` and not `Tuna::Swim()`, even though that base class instance `Fish` is a part of an instance of `Tuna`. This problem is demonstrated in following code

```cpp
#include <iostream>
using namespace std;

class Fish
{
public:
   void Swim()
   {
      cout << "Fish swims!" << endl;
   }
};

class Tuna:public Fish
{
public:
   // override Fish::Swim
   void Swim()
   {
      cout << "Tuna swims!" << endl;
   }
};

void MakeFishSwim(Fish& inputFish)
{
   // calling Fish::Swim
   inputFish.Swim();
}

int main() 
{
   Tuna myDinner;

   // calling Tuna::Swim
   myDinner.Swim();

   // sending Tuna as Fish
   MakeFishSwim(myDinner);

   return 0;
}
```

Output

```
Tuna swims! 
Fish swims!
```

The class `Tuna` specializes the class `Fish` via public inheritance. It also overrides `Fish::Swim()`. `main()` makes a direct call to `Tuna::Swim()`  and passes myDinner (of type `Tuna`) as a parameter to `MakeFishSwim()`, which interprets it as a reference `Fish&`, as shown in its declaration. In other words, `MakeFishSwim(Fish&)` doesn’t care if the object sent was a `Tuna`, handles it as a `Fish`, and invokes `Fish::Swim()`. So, the second line of output indicates that the same object `Tuna` produced the output of a `Fish`, not indicating any specialization thereof (and could as well be a `Carp`).

What the user would ideally expect is that an object of type `Tuna` behaves like a tuna even if the method invoked is `Fish::Swim()`. In other words, when `inputFish.Swim()` is invoked, the user expects it to execute `Tuna::Swim()`. Such polymorphic behavior where an object of base class `Fish` can behave as its actual type; that is, derived class `Tuna` can be implemented by making `Fish::Swim()` a *virtual* function.
