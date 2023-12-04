[//]: #  (###Overloading Functions)

Function overloading in C++ allows multiple functions with the same name to be defined in the same scope, as long as their parameter lists differ in number or types. This enables you to use the same name for different functions based on the parameters they take.

Here's an example demonstrating function overloading:

```cpp
#include <iostream>

// Function to calculate the square of an integer
int square(int num) {
    return num * num;
}

// Overloaded function to calculate the square of a double
double square(double num) {
    return num * num;
}

int main() {
    int intNum = 5;
    double doubleNum = 2.5;

    std::cout << "Square of integer " << intNum << " is: " << square(intNum) << std::endl;
    std::cout << "Square of double " << doubleNum << " is: " << square(doubleNum) << std::endl;

    return 0;
}
```

In this example, there are two functions named `square`, but they differ in the types of their parameters. The first `square` function takes an `int` parameter, while the second `square` function takes a `double` parameter.

When `square` is called in `main()` with an `int` argument (`square(intNum)`), the compiler matches it to the `int` version of `square` and executes that function. Similarly, when `square` is called with a `double` argument (`square(doubleNum)`), the compiler selects the `double` version of `square`.

Function overloading is useful when you want to perform similar operations but with different types of data. It allows for more intuitive and readable code by using the same function name for related operations.
