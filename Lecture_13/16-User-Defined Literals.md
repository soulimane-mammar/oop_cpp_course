[//]: # (### User-Defined Literals)

User-defined literals are a feature introduced in C++11 that enable users to define their own custom suffixes for numeric or string literals. These custom suffixes allow developers to create more expressive and domain-specific code by extending the capabilities of literals.

### Syntax

The syntax for defining a user-defined literal involves creating a function or operator that appends a specific suffix to a literal. The general form is:

```cpp
return_type operator "" suffix_name(ValueType value) {
    // Implementation to process the literal with the specified suffix
}
```

- `return_type`: The type returned after processing the literal with the custom suffix.
- `operator ""`: This literal operator denotes the creation of a user-defined literal.
- `suffix_name`: The name of the custom suffix that will be appended to a literal.
- `arguments`: Optional arguments passed to the operator, specifying the literal's value or metadata.

### Example

```cpp
#include <iostream>
using namespace std;

// Define a user-defined literal for converting meters to kilometers
constexpr long double operator "" _km(long double meters) {
    return meters / 1000.0;
}


struct Temperature
{
   double Kelvin;
   Temperature(long double kelvin) : Kelvin(kelvin) {}
};

Temperature operator"" _C(long double celsius)
{
   return Temperature(celsius + 273);
}

Temperature operator "" _F(long double fahrenheit)
{
   return Temperature((fahrenheit + 459.67) * 5 / 9);
}

int main() {
    // Use the custom suffix "_km" to convert meters to kilometers
    long double distance_km = 5000.0_km;
    
    std::cout << "Distance in kilometers: " << distance_km << std::endl;

   Temperature k1 = 31.73_F;
   Temperature k2 = 0.0_C;

   cout << "k1 is " << k1.Kelvin << " Kelvin" << endl;
   cout << "k2 is " << k2.Kelvin << " Kelvin" << endl;


    return 0;
}
```

In this example, the `_km` suffix is a user-defined literal that converts meters to kilometers. When `5000.0_km` is encountered in the code, the `operator "" _km` function is called, transforming the value accordingly.

We also have two instances of `Temperature`: one using a user-defined literal `_F` to declare an initial value in Fahrenheit and the other using a user-defined literal to declare an initial value in Celsius. Note that `k2` has intentionally been initialized to `0.0_C` and not to `0_C` because the literal `_C` has been defined (and is required) to take a `long double` as input value, and 0 would be interpreted as an integer.

**Note**
Depending on the nature of the user-defined literal, the `ValueType` parameter would be restricted to one of the following:

- `unsigned long long int` for integral literal
- `long double` for floating-point literal
- `char, wchar_t, char16_t, or char32_t` for character literal
