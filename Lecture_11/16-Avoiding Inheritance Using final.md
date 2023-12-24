[//]: # (### Avoiding Inheritance Using final)

There are instances when you need to ensure that absolutely no class can inherit from a class; that is, you want to be sure a particular class cannot be used as a base class. The specifier `final`, introduced with C++11, helps you do exactly this. A class declared as final cannot be used as a base class. For instance, the class Platypus represents a well-evolved species. You may therefore want to ensure that this class is final, thereby blocking every possibility to inherit from it. A version of the class Platypus declared as final would look like this:

```cpp
// declaring class as final ensures that it cannot be derived from
class Platypus final: public Mammal, public Bird, public Reptile
{
public:
   void Swim()
   {
      cout << "Platypus: Voila, I can swim!" << endl;
   }
};
```
