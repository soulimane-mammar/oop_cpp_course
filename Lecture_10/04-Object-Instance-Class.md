[//]:# (###An Object as an Instance of a Class)

In object-oriented programming (OOP), an object is an instance of a class. It's a tangible entity created based on the blueprint defined by the class.

#### Object vs. Class

- **Class:** A class is a blueprint or template that defines the structure, behavior, and properties that objects of that class will have. It encapsulates data and methods.
- **Object:** An object is an instance of a class. It's created using the class blueprint and represents a specific realization of that class, having its own unique data and state.

#### Characteristics of Objects

1. **Properties (Attributes):** Objects have properties or attributes that define their state. These are represented by the member variables defined in the class.

2. **Behavior (Methods):** Objects can perform actions or behaviors. These actions are represented by the member functions defined in the class.

3. **Identity:** Each object has its own identity and state. Even if two objects belong to the same class, they are distinct entities with their own separate data.

#### Example

```cpp
class Car {
private:
    string make;
    string model;
    int year;

public:
    // Constructor to initialize object properties
    Car(string m, string mdl, int yr) : make(m), model(mdl), year(yr) {}

    // Method to display information about the car
    void displayInfo() {
        cout << "Make: " << make << ", Model: " << model << ", Year: " << year << endl;
    }
};

int main() {
    Car myCar("Toyota", "Corolla", 2022); // Creating an object of the Car class
    myCar.displayInfo(); // Accessing the method of the object

    Car yourCar("Kia","Picanto",2012) ; // Creating another object of the Car class
    yourCar.displayInfo() ;

    return 0;
}
```

In this example, `myCar` is an object created from the `Car` class. It has its own distinct `make`, `model`, and `year` attributes, initialized using the class constructor. The `displayInfo()` method is accessed through the object, allowing the object to perform its behavior (displaying information about the car).

Objects are the building blocks of an object-oriented system, enabling the modeling of real-world entities and providing a way to work with data and behaviors in a structured and modular manner.
