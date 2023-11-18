[//]: # (#### Basic Input Using `std::cin` and Output Using `std::cout`)

In C++, `std::cout` and `std::cin` are standard input/output stream objects provided by the C++ Standard Library. They are essential for handling console input and output operations.

`std::cout` is used for output, allowing the display of information to the console, while `std::cin` is used for input, enabling the program to receive data entered by the user.

Here's a simple C++ program that demonstrates basic input using `std::cin` and output using `std::cout`:

```cpp
#include <iostream>

int main() {
    // Declare variables to store user input
    int age;
    std::string name;

    // Get user input for age
    std::cout << "Enter your age: ";
    std::cin >> age;

    // Get user input for name
    std::cout << "Enter your name: ";
    std::cin.ignore();  // Clear the input buffer
    std::getline(std::cin, name);

    // Display the entered information
    std::cout << "Hello, " << name << "! You are " << age << " years old." << std::endl;

    return 0;
}
```

In this program:

- We use `std::cout` to display a prompt and then use `std::cin` to read the user's input.
- For the age, we use `std::cin` directly to get an integer.
- For the name, we use `std::getline` to read a whole line of text, and `std::cin.ignore()` is used to clear any remaining newline characters in the input buffer from the previous input.
