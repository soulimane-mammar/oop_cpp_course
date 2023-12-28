[//]: # (### Using Virtual Inheritance to Solve the Diamond Problem)

Let's  consider the following example:

```cpp
#include <iostream>
using namespace std;

class Animal
{
public:
   Animal()
   {
      cout << "Animal constructor" << endl;
   }

   int age;
};

class Mammal:public Animal {};
class Bird:public Animal {};
class Reptile:public Animal {};

class Platypus :public Mammal, public Bird, public Reptile
{
public:
   Platypus()
   {
      cout << "Platypus constructor" << endl;
   }
};

int main()
{
   Platypus duckBilledP;

   // uncomment next line of code to see compile failure because
   // age is ambiguous: three instances of base Animal per Platypus
   // duckBilledP.age = 25;

   return 0;
}
```

Output

```
Animal constructor 
Animal constructor 
Animal constructor 
Platypus constructor
```

As the output demonstrates, due to multiple inheritance and all three base classes of `Platypus` inheriting in turn from the class `Animal`, you have three instances of `Animal` created automatically for every instance of `Platypus`.

This is ridiculous because `Platypus` is still one animal that has inherited certain attributes from `Mammal`, `Bird`, and `Reptile`.

The problem in the number of instances of base `Animal` is not limited to memory consumption alone. Animal has an integer member `Animal::age`. When you want to access `Animal::age` via an instance of `Platypus`, you get a compilation error simply because the compiler doesn’t know whether you want to set `Mammal::Animal::age` or `Bird::Animal::age` or `Reptile::Animal::age`.

It can get even more ridiculous. If you so wanted, you could set all three:

```cpp
duckBilledP.Mammal::Animal::age = 25; 
duckBilledP.Bird::Animal::age = 2; 
duckBilledP.Reptile::Animal::age = 5;
```

The solution is in **virtual inheritance**.
If you expect a derived class to be used as a base class, it may be a good idea to define its relationship to the base class by using the keyword `virtual`:

```cpp
class Derived1: public virtual Base 
{ 
    // ... members and functions 
}; 
class Derived2: public virtual Base 
{ 
    // ... members and functions 
};
```

The following code shows a better class Platypus

```cpp
#include <iostream>
using namespace std;

class Animal
{
public:
   Animal()
   {
      cout << "Animal constructor" << endl;
   }

   int age;
};

class Mammal:public virtual Animal {};
class Bird:public virtual Animal {};
class Reptile:public virtual Animal {};

class Platypus final:public Mammal, public Bird, public Reptile
{
public:
   Platypus()
   {
      cout << "Platypus constructor" << endl;
   }
};

int main()
{
   Platypus duckBilledP;

   // no compile error as there is only one Animal::age
   duckBilledP.age = 25; 

   return 0;
}
```

Output

```
Animal constructor 
Platypus constructor
```

We can see that the number of instances of the Animal class constructed has fallen to one compared to the previous example.

> **Note**
> A problem caused in an inheritance hierarchy containing two or more base classes that inherit from a common base, which results in the need for ambiguity resolution in the absence of virtual inheritance, is called the **diamond problem**.

The name diamond problem was inspired by the shape of the class diagram.

```
          Animal
       /    |    \
  Mammal   Bird  Reptile
       \    |    /
         Platypus

```
