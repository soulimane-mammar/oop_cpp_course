[//]:# (### What Is a Function Call, and What Are Arguments?)

A function call in C++ is an instruction that tells the program to execute the code within a specific function. When a function is called, the program jumps to that function's definition, executes the code inside it, and then returns to where the function was called.

Arguments, also known as parameters, are the values passed to a function when it's called. These values are used by the function to perform its task. When defining a function, parameters are declared to specify the type and number of values the function expects to receive.

Here's an example of a function call with arguments:

```cpp
#include <iostream>

// Function definition
void greet(std::string name) {
    std::cout << "Hello, " << name << "!" << std::endl;
}

int main() {
    std::string userName = "Alice";

    // Function call with an argument
    greet(userName); // This calls the greet function and passes 'userName' as an argument

    return 0;
}
```

In this example, `greet` is a function that takes a `std::string` parameter named `name`. Inside `main()`, the `greet` function is called with the argument `userName`, which contains the value `"Alice"`. When `greet(userName)` is executed, the program passes the value of `userName` to the `greet` function, and it uses that value to print "Hello, Alice!" to the console.

Functions can take multiple arguments of different types, and these arguments are used within the function to perform specific tasks or calculations.
