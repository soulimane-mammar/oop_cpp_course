[//]: # (### C++ Strings: Using std::string)

`std::string` in C++ from the Standard Library is a versatile and powerful class used for handling strings. Unlike C-style strings, `std::string` provides a safer, more flexible, and feature-rich way of working with text data.

Here's an example demonstrating the usage of `std::string`:

```cpp
#include <iostream>
#include <string> // Include the string library

int main() {
    // Declaration and initialization of std::string
    std::string greeting = "Hello, World!";

    // Output the string
    std::cout << "The greeting is: " << greeting << std::endl;

    // Accessing individual characters
    std::cout << "First character: " << greeting[0] << std::endl;
    std::cout << "Character at index 7: " << greeting[7] << std::endl;

    // Getting the length of the string
    std::cout << "Length of the string: " << greeting.length() << std::endl;

    // Modifying the string
    greeting += " Welcome!"; // Concatenation
    std::cout << "Modified greeting: " << greeting << std::endl;

    // Using string member functions
    std::string sub = greeting.substr(6, 5); // Substring extraction
    std::cout << "Substring: " << sub << std::endl;

    return 0;
}
```

In this example:

- `std::string greeting = "Hello, World!";` initializes a `std::string` object named `greeting` with the content `"Hello, World!"`.
- The `std::string` class provides various member functions like `length()` and `substr()` for operations such as obtaining the length of the string or extracting substrings.
- `+=` is used for string concatenation, allowing easy appending of strings.

`std::string` simplifies string manipulation by managing memory allocation, null termination, and resizing dynamically. It also offers a wide range of member functions for string manipulation and access, making it the preferred choice for handling strings in modern C++ over C-style strings.
