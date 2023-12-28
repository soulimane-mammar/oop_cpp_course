[//]: # (### Polymorphic Behavior Implemented Using Virtual Functions)

We have access to an object of type `Fish`, via pointer `Fish*` or reference `Fish&`. This object could have been instantiated solely as a `Fish`, or it could be part of a `Tuna` or `Carp` that inherits from `Fish`. We don’t know (and don’t care).

We invoke the method `Swim()` using this pointer or reference, like this:

```cpp
pFish->Swim(); 
myFish.Swim(); 
```

What you expect is that the object `Fish` swims as a `Tuna` if it is part of a `Tuna`, as a `Carp` if it is part of a `Carp`, or as an anonymous `Fish` if it wasn’t instantiated as part of a specialized class such as `Tuna` or `Carp`.

We can ensure this by declaring the function `Swim()` in the base class `Fish` as a `virtual` function:

```cpp
class Base 
{ 
    virtual ReturnType FunctionName (Parameter List); 
}; 
class Derived: public Base 
{ 
    ReturnType FunctionName (Parameter List); 
};
```

 Use of the keyword `virtual` means that the compiler ensures that any overriding variant of the requested base class method is invoked. Thus, if `Swim()` is declared `virtual`, invoking `myFish.Swim()` (myFish being of type `Fish&`) results in `Tuna::Swim()` being executed, as demonstrated in the following code.

 ```cpp
 #include <iostream>
using namespace std;

class Fish
{
public:
   virtual void Swim()
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

class Carp:public Fish
{
public:
   // override Fish::Swim
   void Swim()
   {
      cout << "Carp swims!" << endl;
   }
};

void MakeFishSwim(Fish& InputFish)
{
   // calling Swim
   InputFish.Swim();
}

int main() 
{
   Tuna myDinner;
   Carp myLunch;

   // sending Tuna as Fish
   MakeFishSwim(myDinner);

   // sending Carp as Fish
   MakeFishSwim(myLunch);

   return 0;
}
 ```

 Output

 ```
 Tuna swims! 
 Carp swims!
 ```

 The implementation of the function `MakeFishSwim(Fish&)` has not changed. However, the output it produces is dramatically different. For one thing, `Fish::Swim()` has not been invoked at all because of the presence of overriding variants `Tuna::Swim()` and `Carp::Swim()` that have taken priority over `Fish::Swim()` because the latter has been declared as a `virtual` function.
