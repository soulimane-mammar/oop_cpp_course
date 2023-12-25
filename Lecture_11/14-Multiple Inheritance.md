[//]: # (### Multiple Inheritance)

Multiple inheritance  allows a class to inherit from more than one base class. For instance, a platypus is part mammal, part bird, and part reptile. For such cases, C++ allows a class to derive from two or more base classes:

```cpp
class Derived: access-specifier Base1, access-specifier Base2
{
// class members
};
```

The class diagram for the `Platypus` class, is illustrated by figure below
![Platypus Class](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/Lecture_11/platypus.png?raw=true)

Thus, the C++ representation of the class Platypus is as follows:

```cpp
#include <iostream>
using namespace std;

class Mammal
{
public:
   void FeedBabyMilk()
   {
      cout << "Mammal: Baby says glug!" << endl;
   }
};

class Reptile
{
public:
   void SpitVenom()
   {
      cout << "Reptile: Shoo enemy! Spits venom!" << endl;
   }
};

class Bird
{
public:
   void LayEggs()
   {
      cout << "Bird: Laid my eggs, am lighter now!" << endl;
   }
};

class Platypus : public Mammal, public Bird, public Reptile
{
public:
   void Swim()
   {
      cout << "Platypus: Voila, I can swim!" << endl;
   }
};

int main() 
{
   Platypus realFreak;
   realFreak.LayEggs();
   realFreak.FeedBabyMilk();
   realFreak.SpitVenom();
   realFreak.Swim();

   return 0;
}
```

Output

```
Bird: Laid my eggs, am lighter now! 
Mammal: Baby says glug! 
Reptile: Shoo enemy! Spits venom! 
Platypus: Voila, I can swim!
```

The `Platypus` class essentially does nothing more than inherit from the three classes: `Mammal`, `Reptile`, and `Bird`. `main()` is able to invoke these three characteristics of the individual base classes using an object of the derived class `Platypus`. In addition to invoking the inherited functions, `main()` also invokes `Platypus::Swim()`. This program demonstrates the syntax of multiple inheritance and also how a derived class exposes all the public attributes (in this case public member functions) of its many base classes.
