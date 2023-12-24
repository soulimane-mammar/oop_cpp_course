[//]: # (### Order of Construction and Destruction)

## Order of Construction

The order of construction is crucial when dealing with inheritance and class hierarchies. Here's a summary:

1. **Base Class Constructor:** The base class constructor is called before the derived class constructor.

2. **Virtual Base Classes:** If a class inherits from multiple base classes, and these base classes share a common virtual base class, the virtual base class constructor is called only once, ensuring there's a single instance of the shared base class.

3. **Order of Initialization:** Within a derived class constructor, base class constructors are invoked in the order in which they appear in the inheritance list, regardless of the order they are listed in the constructor's initialization list.

4. **Member Object Initialization:** Member objects within a class are initialized in the order they are declared in the class, regardless of their order in the initialization list.

For example:

```cpp
class Base {
public:
    Base() {
        // Base class constructor
    }
};

class Derived : public Base {
private:
    AnotherClass obj1;
    YetAnotherClass obj2;
public:
    Derived() : Base(), obj1(), obj2() {
        // Derived class constructor
    }
};
```

In this scenario, the order of construction would be: `Base` constructor, `obj1`, `obj2`, and finally, the `Derived` constructor body.

## Order of Destruction

[//]: # (### Order of Destruction)

The order of destruction follows the reverse order of construction for both base classes and member objects:

1. **Member Object Destruction:** Member objects within a class are destructed in the reverse order of their construction, meaning the last member to be constructed is the first one to be destructed.

2. **Derived Class Destruction:** After member objects, the destructor of the derived class is called. This happens before the destructor of its base class.

3. **Base Class Destruction:** Finally, the base class destructor is called after the derived class destructor. If there's a hierarchy of base classes, destructors are called in the order of inheritance, from the most derived class to its base classes.

For example:

```cpp
class Base {
public:
    ~Base() {
        // Base class destructor
    }
};

class Derived : public Base {
private:
    AnotherClass obj1;
    YetAnotherClass obj2;
public:
    ~Derived() {
        // Derived class destructor
    }
};
```

In this scenario, during destruction, the order would be: `obj2`, `obj1`, `Derived` class destructor, and finally, `Base` class destructor.

## Example

```cpp
#include <iostream>
using namespace std; 

class FishDummyMember
{
public:
   FishDummyMember()
   {
      cout << "FishDummyMember constructor" << endl;
   }

   ~FishDummyMember()
   {
      cout << "FishDummyMember destructor" << endl;
   }
};

class Fish
{
protected:
   FishDummyMember dummy;

public:
   // Fish constructor
   Fish()
   {
      cout << "Fish constructor" << endl;
   }

   ~Fish()
   {
      cout << "Fish destructor" << endl;
   }
};

class TunaDummyMember
{
public:
   TunaDummyMember()
   {
      cout << "TunaDummyMember constructor" << endl;
   }

   ~TunaDummyMember()
   {
      cout << "TunaDummyMember destructor" << endl;
   }
};

class Tuna: public Fish
{
private:
   TunaDummyMember dummy;

public:
   Tuna()
   {
      cout << "Tuna constructor" << endl;
   }
   ~Tuna()
   {
      cout << "Tuna destructor" << endl;
   }

};
   
int main()
{
   Tuna myDinner;
}
```

Output

```
FishDummyMember constructor
Fish constructor
TunaDummyMember constructor
Tuna constructor
Tuna destructor
TunaDummyMember destructor
Fish destructor
FishDummyMember destructor
```

The output indicates that when an object of the class `Tuna` is instantiated, instantiation actually starts at the top of the hierarchy. So, the base class `Fish` part of the class `Tuna` is instantiated first, and in the process, the members of the class Fish —that is, `Fish::dummy`—are instantiated first. This is then followed by the constructor of the class `Fish`, which is rightfully executed after the member attributes such as dummy have been constructed. After the base class has been constructed, the instantiation of `Tuna` continues first with instantiation of the member `Tuna::dummy`, followed by the execution of the constructor code in `Tuna::Tuna()`. The output demonstrates that the sequence of destruction is exactly the reverse.
