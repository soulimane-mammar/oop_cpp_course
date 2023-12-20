[//]: # (### The Copy Constructor)

The copy constructor in C++ is a special constructor that initializes a new object as a copy of an existing object of the same class. It is used to create a new object with the same data as an existing object, providing a mechanism for object replication.

#### Characteristics of Copy Constructors

1. **Same Class Parameter:** Copy constructors take a reference to an object of the same class as a parameter.

2. **Creates a Replica:** They create a new object by initializing it with the data of an existing object passed as an argument.

3. **Default Copy Constructor:** If a class doesn’t define its own copy constructor, the compiler generates a default copy constructor, which performs a shallow copy of member variables.

#### When Is the Copy Constructor Used?

- **Initialization:** When a new object is initialized using another object of the same class.
  
- **Passing Objects by Value:** When objects are passed as arguments to functions by value rather than by reference.

- **Returning Objects by Value:** When a function returns an object by value.

#### Example of a Copy Constructor

```cpp
#include <iostream>
using namespace std;

class Car {
private:
    string make;
    string model;

public:
    // Parameterized constructor
    Car(string carMake, string carModel) : make(carMake), model(carModel) {}

    // Copy constructor
    Car(const Car &otherCar) : make(otherCar.make), model(otherCar.model) {
        cout << "Copy constructor called." << endl;
    }

    // Display method to show car details
    void displayInfo() {
        cout << "Make: " << make << ", Model: " << model << endl;
    }
};

int main() {
    Car originalCar("Toyota", "Corolla"); // Creating an original object
    originalCar.displayInfo(); // Output: Make: Toyota, Model: Corolla

    Car copiedCar = originalCar; // Using the copy constructor to create a copy
    copiedCar.displayInfo(); // Output: Make: Toyota, Model: Corolla

    return 0;
}
```

In this example:

- The `Car` class has a copy constructor `Car(const Car &otherCar)` that initializes a new `Car` object with the data of another `Car` object.
- `Car copiedCar = originalCar;` invokes the copy constructor to create `copiedCar` as a copy of `originalCar`.

The copy constructor allows objects to be copied efficiently, ensuring that a new object is created with the same data as an existing object. Customizing the copy constructor can be beneficial for classes that manage resources or require deep copying of dynamic memory to avoid issues related to shallow copying.
