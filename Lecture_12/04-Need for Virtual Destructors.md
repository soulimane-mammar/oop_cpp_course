[//]: # (### Need for Virtual Destructors)

Let's look at the following code

```cpp
#include <iostream>
using namespace std;

class Fish
{
public:
   Fish()
   {
      cout << "Constructed Fish" << endl;
   }
   ~Fish()
   {
      cout << "Destroyed Fish" << endl;
   }
};

class Tuna:public Fish
{
public:
   Tuna()
   {
      cout << "Constructed Tuna" << endl;
   }
   ~Tuna()
   {
      cout << "Destroyed Tuna" << endl;
   }
};

void DeleteFish(Fish* pFish)
{
   delete pFish;
}

int main() 
{
   cout << "Allocating a Tuna on the free store:" << endl;
   Tuna* pTuna = new Tuna;
   cout << "Deleting the Tuna: " << endl;
   DeleteFish(pTuna);

   cout << "Instantiating a Tuna on the stack:" << endl;
   Tuna myDinner;
   cout << "Automatic destruction as it goes out of scope: " << endl;

   return 0;
}
```

Output

```
Allocating a Tuna on the free store:
Constructed Fish 
Constructed Tuna 
Deleting the Tuna: 
Destroyed Fish 
Instantiating a Tuna on the stack: 
Constructed Fish 
Constructed Tuna 
Automatic destruction as it goes out of scope: 
Destroyed Tuna 
Destroyed Fish
```

`main()` creates an instance of `Tuna` on the free store, using `new`, and then releases the allocated memory by using the service function `DeleteFish()` . For the sake of comparison, another instance of `Tuna` is created as a local variable `myDinner` on the stack and goes out of scope when `main()` ends. The output is created by the `cout` statements in the constructors and destructors of classes `Fish` and `Tuna`. Note that while `Tuna` and therefore `Fish` were both constructed on the free store because of the operator `new`, the destruction of allocated memory by `DeleteFish()` was partial. Destructor of `Tuna` was not invoked during delete; rather, only the destruction of `Fish` was invoked. This is in stark contrast to the construction and destruction of local member `myDinner`, where all constructors and destructors are invoked. We saw in Lesson 10 the correct order of construction and destruction of classes in an inheritance hierarchy, and that all destructors need to be invoked, including `~Tuna()`.

This flaw means that the destructor of a deriving class that has been instantiated on the free store using `new` would not be invoked if `delete` is called using a pointer of type `Base*`. This can result in resources not being released, memory leaks, and so on and is a problem that is not to be taken lightly.

To avoid this problem, you use virtual destructors, as illustrated in following code

```cpp
#include <iostream>
using namespace std;

class Fish
{
public:
   Fish()
   {
      cout << "Constructed Fish" << endl;
   }
   virtual ~Fish()   // virtual destructor!
   {
      cout << "Destroyed Fish" << endl;
   }
};

class Tuna:public Fish
{
public:
   Tuna()
   {
      cout << "Constructed Tuna" << endl;
   }
   ~Tuna()
   {
      cout << "Destroyed Tuna" << endl;
   }
};

void DeleteFishMemory(Fish* pFish)
{
   delete pFish;
}

int main() 
{
   cout << "Allocating a Tuna on the free store:" << endl;
   Tuna* pTuna = new Tuna;
   cout << "Deleting the Tuna: " << endl;
   DeleteFishMemory(pTuna);

   cout << "Instantiating a Tuna on the stack:" << endl;
   Tuna myDinner;
   cout << "Automatic destruction as it goes out of scope: " << endl;

   return 0;
}
```

Output

```
Allocating a Tuna on the free store: 
Constructed Fish 
Constructed Tuna 
Deleting the Tuna:
Destroyed Tuna 
Destroyed Fish 
Instantiating a Tuna on the stack: 
Constructed Fish 
Constructed 
Tuna Automatic destruction as it goes out of scope: 
Destroyed Tuna 
Destroyed Fish
```

> **Note**
> Always declare the base class destructor as `virtual`.
