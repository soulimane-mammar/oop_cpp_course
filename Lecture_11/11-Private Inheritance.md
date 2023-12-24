[//]: # (### Private Inheritance)

Private inheritance in C++ is a form of inheritance where the public and protected members of the base class become private members of the derived class. Here's a breakdown:

1. **Syntax:**

   ```cpp
   class Base {
   public:
       void publicMethod() {
           // Public method in Base
       }
       int publicData;
   };

   class Derived : private Base {
       // Access specifier 'private' for inheritance
       // All public and protected members of Base become private in Derived
   public:
       void accessBase() {
           publicMethod();  // Accessible within Derived
           int data = publicData;  // Accessible within Derived
       }
   };
   ```

1. **Usage:**
   - Private inheritance is used when the derived class wants to utilize the implementation of a base class but does not need to expose that relationship publicly.
   - It's often used for implementation purposes rather than establishing an "is-a" relationship.

#### Example

```cpp
#include <iostream>
using namespace std;

class Motor
{
public:
   void SwitchIgnition()
   {
      cout << "Ignition ON" << endl;
   }
   void PumpFuel()
   {
      cout << "Fuel in cylinders" << endl;
   }
   void FireCylinders()
   {
      cout << "Vroooom" << endl;
   }
};

class Car:private Motor
{
public:
   void Move()
   {
      SwitchIgnition();
      PumpFuel();
      FireCylinders();
   }
};

int main()
{
   Car myDreamCar;
   myDreamCar.Move();

   return 0;
}
```

Output

```
Ignition ON
Fuel in cylinders
Vroooom
```

The class `Motor` has three public member functions that switch ignition, pump fuel, and fire the cylinders. The class `Car` inherits from `Motor`, using the keyword `private`. Thus, the public function `Car::Move()` invokes members from the base class `Motor`. If you try inserting the following `in main()`:

```cpp
myDreamCar.PumpFuel(); // cannot access base’s public member
```

it fails compilation with an error similar to error C2247: Motor::PumpFuel not accessible because 'Car’ uses ’private’ to inherit from ’Motor.’
