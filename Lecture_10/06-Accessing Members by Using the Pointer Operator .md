[//]: # (### Accessing Members by Using the Pointer Operator)

The arrow operator (`->`) is used to access members (attributes and methods) of an object through a pointer to that object. When you have a pointer to an object, the arrow operator provides a way to reference and manipulate the members of that object.

#### Accessing Attributes via Pointer

```cpp
class Car {
public:
    string make;
    string model;
    int year;
};

int main() {
    Car* myCarPtr = new Car(); // Creating a pointer to an object of the Car class

    // Accessing and assigning values to object's attributes using the arrow operator
    myCarPtr->make = "Toyota";
    myCarPtr->model = "Corolla";
    myCarPtr->year = 2022;

    delete myCarPtr; // Don't forget to deallocate memory

    return 0;
}
```

In this example, the arrow operator (`->`) is used to assign values to the `make`, `model`, and `year` attributes of the object pointed to by `myCarPtr`.

#### Calling Methods via Pointer

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
    Car* myCarPtr = new Car(); // Creating a pointer to an object of the Car class

    // Accessing and calling a method using the arrow operator
    myCarPtr->displayInfo();

    delete myCarPtr; // Don't forget to deallocate memory

    return 0;
}
```

Here, the arrow operator is used to call the `displayInfo()` method of the object pointed to by `myCarPtr`, displaying information about the car.

#### Key Points

- The arrow operator (`->`) is used specifically with pointers to objects to access their members.
- It is a shorthand notation for dereferencing the pointer and accessing the members directly.
- The arrow operator provides an indirect way to access members of objects when working with pointers to those objects.
