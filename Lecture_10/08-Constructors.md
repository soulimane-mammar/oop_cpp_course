[//]: # (### Constructors)

Constructors in C++ are special member functions within a class that are automatically invoked when an object of that class is created. They initialize the object's data members or perform other necessary setup operations.

#### Characteristics of Constructors

1. **Same Name as Class:** Constructors have the same name as the class they belong to and do not have a return type, not even `void`.

2. **Initialization:** They initialize the object's data members, allocate resources, or perform any necessary setup when an object is created.

3. **Automatically Called:** Constructors are called implicitly when an object is instantiated and cannot be called explicitly like regular functions.

4. **Multiple Constructors:** A class can have multiple constructors (overloaded constructors) with different parameter lists, enabling object creation with varying sets of arguments.

5. **Default Constructor:** If no constructors are defined within a class, C++ provides a default constructor (with no parameters) that initializes member variables to default values.

#### Types of Constructors

1. **Default Constructor:** Takes no arguments and is automatically called when an object is created without any parameters.

2. **Parameterized Constructor:** Accepts parameters to initialize an object's member variables based on the provided arguments.

3. **Copy Constructor:** Constructs a new object as a copy of an existing object of the same class.

### Example of Constructors

```cpp
class Car {
private:
    string make;
    string model;
    int year;

public:
    // Parameterized constructor
    Car(string carMake, string carModel, int carYear) {
        make = carMake;
        model = carModel;
        year = carYear;
    }

    // Default constructor
    Car() {
        make = "Unknown";
        model = "Unknown";
        year = 0;
    }

    // Copy constructor
    Car(const Car &otherCar) {
        make = otherCar.make;
        model = otherCar.model;
        year = otherCar.year;
    }
};

int main() {
    Car myCar("Toyota", "Corolla", 2022); // Using the parameterized constructor

    Car defaultCar; // Using the default constructor

    Car copiedCar = myCar; // Using the copy constructor

    return 0;
}
```

In this example, the `Car` class has multiple constructors: a parameterized constructor, a default constructor, and a copy constructor. Depending on how the objects are created (`myCar`, `defaultCar`, `copiedCar`), different constructors are invoked to initialize the objects.
