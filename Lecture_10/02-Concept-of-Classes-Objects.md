[//]: #  (###The Concept of Classes and Objects)

In object-oriented programming (OOP), classes and objects are fundamental concepts used to model real-world entities and encapsulate data and behavior.

#### Classes

- **Blueprints or Templates:** Classes serve as blueprints or templates for creating objects. They define the structure, behavior, and properties that objects of that class will have.
- **Data and Functions:** Classes encapsulate data (attributes or member variables) and functions (methods or member functions) that operate on that data.
- **Abstraction:** They provide a way to abstract complex real-world entities into manageable and reusable code components.
- **Example:** Consider a `Car` class that defines attributes like `make`, `model`, `year`, and methods like `startEngine()` or `drive()`.

#### Objects

- **Instances of Classes:** Objects are instances of classes. They are tangible entities created based on the structure defined by a class.
- **Properties and Behavior:** Objects have properties (values for the attributes defined in the class) and behavior (actions performed using the methods defined in the class).
- **Example:** An object `myCar` created from the `Car` class might have specific values for `make`, `model`, and `year`, and can perform actions like `startEngine()` and `drive()`.

#### Key Concepts

- **Encapsulation:** Classes encapsulate data and methods, hiding the internal workings and exposing only the necessary interfaces.
- **Inheritance:** Classes can inherit properties and behavior from other classes, forming a hierarchical relationship. This allows for code reuse and hierarchy.
- **Polymorphism:** Objects of different classes can be treated as objects of a common superclass through inheritance, enabling flexibility and extensibility in code design.
- **Access Control:** Classes can define access levels (public, private, protected) for their members, controlling how they can be accessed from outside the class.

#### Example

```cpp
// Class definition
class Car {
private:
    string make;
    string model;
    int year;

public:
    // Constructor
    Car(string m, string mdl, int yr) : make(m), model(mdl), year(yr) {}

    // Method to start the engine
    void startEngine() {
        cout << "Engine started!" << endl;
    }

    // Method to drive the car
    void drive() {
        cout << "Car is being driven." << endl;
    }
};

// Creating an object (instance) of the Car class
int main() {
    Car myCar("Toyota", "Corolla", 2022); // Creating an object of type Car
    myCar.startEngine(); // Invoking methods on the object
    myCar.drive();

    return 0;
}
```

In this example, `Car` is a class that encapsulates properties (make, model, year) and behavior (startEngine, drive). An object `myCar` is created from the `Car` class, and methods are invoked on this object to perform actions. This showcases the relationship between classes and objects in C++.
