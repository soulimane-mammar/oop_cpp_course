[//]: # (### Using Constructors to Convert Types)

Constructors can be used to convert one type to another, a process known as a type conversion or conversion constructor. This is achieved by defining a constructor that takes a single argument of a different type, allowing an implicit conversion between the two types.

#### Example of a Conversion Constructor

```cpp
#include <iostream>
using namespace std;

class Centimeters {
private:
    double cmValue;

public:
    // Constructor that converts meters to centimeters
    Centimeters(double meters) : cmValue(meters * 100.0) {}

    // Getter method
    double getCentimeters() const {
        return cmValue;
    }
};

int main() {
    double meters = 2.5;
    
    // Using the conversion constructor to convert meters to centimeters
    Centimeters cm = meters; // Implicit conversion from double to Centimeters
    
    cout << "Meters: " << meters << " converted to Centimeters: " << cm.getCentimeters() << endl;

    return 0;
}
```

In this example:

- The `Centimeters` class has a constructor that takes a `double` (representing meters) and converts it to centimeters.
- When `meters` (which is a `double`) is assigned to `Centimeters cm`, the compiler implicitly calls the conversion constructor to convert the `double` value to a `Centimeters` object.
- The conversion constructor converts the given meters to centimeters and initializes the `Centimeters` object.

Implicit conversions, while convenient in some cases, can sometimes lead to unexpected behavior or errors. To prevent implicit conversions, you can use the `explicit` keyword in front of constructors. This will restrict the constructor from being used for implicit conversions, allowing only explicit conversions through constructor calls.

#### Example Using `explicit` to Prevent Implicit Conversions

```cpp
#include <iostream>
using namespace std;

class Centimeters {
private:
    double cmValue;

public:
    // Explicit constructor that converts meters to centimeters
    explicit Centimeters(double meters) : cmValue(meters * 100.0) {}

    // Getter method
    double getCentimeters() const {
        return cmValue;
    }
};

int main() {
    double meters = 2.5;
    
    // Attempting to use the explicit conversion constructor directly results in a compilation error
    // Centimeters cm = meters; // Error: Conversion from 'double' to 'Centimeters' is ambiguous

    // Explicitly calling the constructor to perform the conversion
    Centimeters cm = Centimeters(meters); // Explicit conversion from double to Centimeters
    
    cout << "Meters: " << meters << " converted to Centimeters: " << cm.getCentimeters() << endl;

    return 0;
}
```

In this updated example:

- The `explicit` keyword is used in the constructor `Centimeters(double meters)` to prevent implicit conversions from `double` to `Centimeters`.
- Attempting to assign `meters` directly to `Centimeters cm` results in a compilation error due to the explicit specifier. The compiler prevents implicit conversions.
- Instead, an explicit call to the constructor is made to perform the conversion.
