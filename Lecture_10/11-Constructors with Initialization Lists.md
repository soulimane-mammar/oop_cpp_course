[//]: # (### Constructors with Initialization Lists)

Initialization lists are used in constructors to initialize class member variables before the body of the constructor executes. Initialization lists provide a more efficient way to initialize members, especially for non-default constructors and for members that are objects or constants.

#### Example of Constructors with Initialization Lists

```cpp
#include <iostream>
using namespace std;

class Car {
private:
    string make;
    string model;
    int year;

public:
    // Parameterized constructor with initialization list
    Car(string carMake, string carModel, int carYear) : make(carMake), model(carModel), year(carYear) {
        // Constructor body can have additional logic if needed
        // This example does not require additional logic
    }

    // Display method to show car details
    void displayInfo() {
        cout << "Make: " << make << ", Model: " << model << ", Year: " << year << endl;
    }
};

int main() {
    Car myCar("Toyota", "Corolla", 2022); // Using parameterized constructor with initialization list
    myCar.displayInfo(); // Output: Make: Toyota, Model: Corolla, Year: 2022

    return 0;
}
```

In this example, the `Car` class's parameterized constructor uses an initialization list to directly initialize the member variables `make`, `model`, and `year`. This approach is preferred, especially when initializing class members that are objects or constants, as it can improve efficiency and avoid unnecessary default construction and assignment.

- `Car(string carMake, string carModel, int carYear) : make(carMake), model(carModel), year(carYear) { ... }` initializes `make`, `model`, and `year` directly in the initialization list.

Using initialization lists in constructors is a recommended practice in C++, particularly when initializing members that are objects or when there are performance considerations, as it can result in more efficient code execution.
