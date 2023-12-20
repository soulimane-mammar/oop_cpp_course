[//]: # (#### Constructor Parameters with Default Values)

In C++, you can assign default values to constructor parameters, allowing objects to be created with fewer arguments. This feature simplifies object creation by providing default values for some or all of the constructor's parameters.

#### Example of Constructor Parameters with Default Values

```cpp
#include <iostream>
using namespace std;

class Car {
private:
    string make;
    string model;
    int year;

public:
    // Parameterized constructor with default parameter values
    Car(string carMake = "Unknown", string carModel = "Unknown", int carYear = 0) {
        make = carMake;
        model = carModel;
        year = carYear;
    }

    // Display method to show car details
    void displayInfo() {
        cout << "Make: " << make << ", Model: " << model << ", Year: " << year << endl;
    }
};

int main() {
    Car defaultCar; // Using default values for all parameters
    defaultCar.displayInfo(); // Output: Make: Unknown, Model: Unknown, Year: 0

    Car customCar("Toyota", "Corolla"); // Using default value for year
    customCar.displayInfo(); // Output: Make: Toyota, Model: Corolla, Year: 0

    return 0;
}
```

In this example, the `Car` class's constructor has default parameter values assigned to `carMake`, `carModel`, and `carYear`. If no arguments are provided during object creation, these default values are used.

- `Car defaultCar;` creates a `Car` object using the default values for all parameters.
- `Car customCar("Toyota", "Corolla");` creates a `Car` object with the provided make and model values and uses the default value (0 in this case) for the year.
