[//]: # (###Functions with Multiple Return Statements)

Functions in C++ can contain multiple return statements, each of which provides a way to exit the function and return a value. The function will return the value specified by the return statement encountered first during the execution flow.

Here's an example demonstrating a function with multiple return statements:

```cpp
#include <iostream>

// Function to determine if a number is positive, negative, or zero
std::string checkNumber(int num) {
    if (num > 0) {
        return "Positive";  // First return statement
    } else if (num < 0) {
        return "Negative";  // Second return statement
    } else {
        return "Zero";      // Third return statement
    }
}

int main() {
    int number = -10;
    std::string result = checkNumber(number);
    std::cout << "The number is: " << result << std::endl;
    return 0;
}
```

In this example, the function `checkNumber` takes an integer `num` as an argument and determines whether it's positive, negative, or zero. The function has three return statements: one for each possible condition (`num > 0`, `num < 0`, and `num == 0`).

When `checkNumber` is called in `main()` with `number` as `-10`, the function evaluates `num < 0` as true, encounters the second return statement (`return "Negative";`), and returns the string `"Negative"`. Thus, `"The number is: Negative"` will be printed to the console.

It's important to note that once a return statement is executed in a function, the function exits immediately, and any subsequent code within the function is not executed. Therefore, only one return statement will be executed during each function call.
