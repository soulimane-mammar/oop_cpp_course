[//]:# (### Function Parameters with Default Values)

In C++, you can provide default values for function parameters. Default parameter values allow you to define a parameterized function where some or all of the parameters have default values assigned. If no argument is provided for those parameters during function invocation, the default values are used.

Here's an example:

```cpp
#include <iostream>

// Function definition with default parameter values
void greet(std::string name = "Guest", int age = 25) {
    std::cout << "Hello, " << name << "! Your age is " << age << " years old." << std::endl;
}

int main() {
    // Calling the function with no arguments
    greet(); // Output: Hello, Guest! Your age is 25 years old.

    // Calling the function with one argument
    greet("Alice"); // Output: Hello, Alice! Your age is 25 years old.

    // Calling the function with both arguments
    greet("Bob", 30); // Output: Hello, Bob! Your age is 30 years old.

    return 0;
}
```

In the `greet` function, both `name` and `age` parameters have default values assigned. If you call `greet()` without passing any arguments, it uses the default values ("Guest" and 25) for `name` and `age` respectively.

You can also selectively override the default values by providing arguments. For instance, `greet("Alice")` uses the default value for `age` (25) while specifying a different name, and `greet("Bob", 30)` overrides both the default `name` and `age`.

Default parameter values are helpful in cases where you want to provide a commonly used value for a parameter, reducing the need to specify it every time the function is called.

> **Note:**
> You can have multiple parameters with default values; however, they should all be at the tail end of the parameters list.
