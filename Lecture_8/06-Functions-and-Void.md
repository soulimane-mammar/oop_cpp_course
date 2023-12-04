[//]:# (### Programming Functions with No Parameters or No Return Values)

Functions can exist without parameters or return values.

#### Function with No Parameters and No Return Value

```cpp
#include <iostream>

// Function definition with no parameters and no return value
void greet() {
    std::cout << "Hello! Have a great day!" << std::endl;
}

int main() {
    // Calling the function with no arguments
    greet(); // Output: Hello! Have a great day!

    return 0;
}
```

Here, `greet()` is a function that doesn't take any parameters and doesn't return any value (`void`). It simply prints a greeting message when called. In the `main()` function, `greet()` is called without passing any arguments.

#### Function with Parameters but No Return Value

```cpp
#include <iostream>

// Function definition with parameters and no return value
void sum(int a, int b) {
    int result = a + b;
    std::cout << "Sum of " << a << " and " << b << " is: " << result << std::endl;
}

int main() {
    int num1 = 5, num2 = 7;

    // Calling the function with arguments but no return value
    sum(num1, num2); // Output: Sum of 5 and 7 is: 12

    return 0;
}
```

In this example, `sum(int a, int b)` is a function that takes two integers as parameters. It calculates their sum and prints the result. The function doesn't return anything (`void`). When called in `main()`, it adds `num1` and `num2` without returning the result.
