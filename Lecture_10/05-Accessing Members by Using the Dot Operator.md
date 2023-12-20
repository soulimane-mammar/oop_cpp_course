[//]: # (### Accessing Members by Using the Dot Operator)

In C++, the dot operator (`.`) is used to access members (attributes and methods) of an object. Once an object is created from a class, the dot operator allows you to reference and manipulate its members.

#### Accessing Attributes

```cpp
class Car {
public:
    string make;
    string model;
    int year;
};

int main() {
    Car myCar; // Creating an object of the Car class

    // Accessing and assigning values to object's attributes using the dot operator
    myCar.make = "Toyota";
    myCar.model = "Corolla";
    myCar.year = 2022;

    return 0;
}
```

In this example, the dot operator (`.`) is used to assign values to the `make`, `model`, and `year` attributes of the `myCar` object.

#### Calling Methods

```cpp
class Car {
public:
    string make;
    string model;
    int year;

    void displayInfo() {
        cout << "Make: " << make << ", Model: " << model << ", Year: " << year << endl;
    }
};

int main() {
    Car myCar; // Creating an object of the Car class

    // Accessing and calling a method using the dot operator
    myCar.displayInfo();

    return 0;
}
```

In this case, the dot operator is used to call the `displayInfo()` method of the `myCar` object, which displays information about the car.

#### Key Points

- The dot operator (`.`) is used exclusively with objects to access their attributes and methods.
- It provides direct access to the members of an object declared from a class.
- It is essential to use the dot operator with the correct object instance to access its specific members.
