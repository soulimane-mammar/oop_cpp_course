[//]: # (###Lambda Functions)

Lambda functions, also called lambda expressions, introduced in C++11, are a concise way to create anonymous functions in-place. They are particularly useful for short, one-off functions or when passing functions as arguments to other functions.

Here's an example of a simple lambda function:

```cpp
#include <iostream>

int main() {
    // Lambda function to add two numbers
    auto add = [](int a, int b) {
        return a + b;
    };

    int result = add(5, 7); // Calling the lambda function
    std::cout << "The result is: " << result << std::endl;

    return 0;
}
```

In this example:

- `[]` defines the lambda's capture list. It can be used to capture variables from the surrounding scope.
- `(int a, int b)` is the parameter list.
- `return a + b;` is the function body.

Lambda functions can also capture variables from their enclosing scope:

```cpp
#include <iostream>

int main() {
    int x = 5;
    int y = 3;

    // Lambda function capturing 'x' by value and 'y' by reference
    auto multiply = [x, &y]() {
        return x * y;
    };

    int result = multiply(); // Calling the lambda function
    std::cout << "The result is: " << result << std::endl;

    return 0;
}
```

In this case:

- `[x, &y]` captures `x` by value and `y` by reference. Changes made to `y` within the lambda will affect the original variable.

Lambda functions are often used in scenarios where you need a short, disposable function, such as when working with algorithms that accept function objects or when defining callbacks in event-driven programming. They provide a way to write functions directly where they are needed, promoting cleaner and more readable code.

>**Note**
>This section provides an introduction to a concept that’s not exactly easy for beginners. So, skim through it and try to learn the concept but don’t be disappointed if you don’t grasp it all. The topic is discussed in depth in a subsequent lecture
