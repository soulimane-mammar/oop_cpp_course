[//]: # (### Protected Inheritance)

Protected inheritance in C++ is an inheritance type where public and protected members of the base class become protected members of the derived class.

1. **Syntax:**

   ```cpp
   class Base {
   public:
       void publicMethod() {
           // Public method in Base
       }
       int publicData;
   };

   class Derived : protected Base {
       // Access specifier 'protected' for inheritance
       // Public and protected members of Base become protected in Derived
   public:
       void accessBase() {
           publicMethod();  // Accessible within Derived
           int data = publicData;  // Accessible within Derived
       }
   };
   ```

1. **Usage:**
  Protected inheritance is similar to private inheritance in the following ways:

   - It also signifies a has-a relationship.
   - It also lets the derived class access all public and protected members of Base.
   - Those outside the inheritance hierarchy with an instance of `Derived` cannot access public members of `Base`.

    However, protected inheritance is a bit different when it comes to the derived class being inherited from:

    ```cpp
    class Derived2: protected Derived
    {
    // can access public & protected members of Base
    };
    ```

    The protected inheritance hierarchy allows the subclass of the subclass (that is, `Derived2`) access to public and protected members of the `Base` class. This would not be possible if the inheritance between Derived and Base were private

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

class Car :protected Motor
{
public:
   void Move()
   {
      SwitchIgnition();
      PumpFuel();
      FireCylinders();
   }
};

class RaceCar :protected Car
{
public:
   void Move()
   {
      SwitchIgnition();  // RaceCar has access to members of
      PumpFuel();  // base Motor due to "protected" inheritance
      FireCylinders(); // between RaceCar & Car, Car & Motor
      FireCylinders();
      FireCylinders();
   }
};

int main()
{
   RaceCar myDreamCar;
   myDreamCar.Move();

   return 0;
}
```

Output

```
Ignition ON
Fuel in cylinders
Vroooom
Vroooom
Vroooom
```

The class `Car` inherits using protected from `Motor`. The class `RaceCar`
inherits using protected from the class `Car` using protected. As you
can see, the implementation of `RaceCar::Move()` uses public methods defined in the base class `Motor`. This access to the ultimate base class Motor via intermediate base class `Car` is governed by the relationship between `Car` and `Motor`. If this were private instead of protected,
`RaceCar` would have no access to the public members of `Motor` as the compiler would choose the most restrictive of the relevant access specifiers. Note that the nature of the relationship between the classes `Car` and `RaceCar` plays no role in access to the base class `Motor`, while the relationship between `Car` and `Motor` does.
