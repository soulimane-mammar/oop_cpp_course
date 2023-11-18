[//]: # (#### Functions in C++)

#### Functions in C++

In C++, functions are blocks of code that perform a specific task. They are fundamental to structured programming and enable code reuse, modularity, and abstraction.

Here's a simple C++ program that includes functions:

```cpp
#include <iostream>

// Function Declaration
int add(int a, int b);
void displayMessage();

// Main Function
int main() {
    // Function Call
    int sum = add(3, 5);

    // Display Result
    std::cout << "Sum: " << sum << std::endl;

    // Function Call
    displayMessage();

    return 0;
}

// Function Definition
int add(int a, int b) {
    return a + b;
}

// Function Definition
void displayMessage() {
    std::cout << "Hello, this is a simple message!" << std::endl;
}
```

In this program:

- The `add` function takes two integers as parameters and returns their sum.
- The `displayMessage` function takes no parameters and doesn't return any value; it simply prints a message to the console.
- In the `main` function, we call `add` to compute the sum of 3 and 5 and then call `displayMessage` to print a message. The results are displayed in the console.

Here are key aspects of functions in C++:

1. **Function Declaration:**
   - A function is declared using the `returnType functionName(parameters)` syntax.

     ```cpp
     int add(int a, int b);
     ```

2. **Function Definition:**
   - The function definition contains the actual code that executes when the function is called.

     ```cpp
     int add(int a, int b) {
         return a + b;
     }
     ```

3. **Return Type:**
   - Functions have a return type indicating the type of value they return. Use `void` if the function doesn't return a value.

     ```cpp
     int add(int a, int b); // int is the return type
     void displayMessage(); // void means no return value
     ```

4. **Parameters:**
   - Functions can take parameters (inputs) to process. Parameters are defined within the parentheses.

     ```cpp
     int add(int a, int b); // a and b are parameters
     ```

5. **Function Call:**
   - To execute a function, you call it by its name and provide actual values for its parameters.

     ```cpp
     int sum = add(3, 5); // Calls the add function with arguments 3 and 5
     ```

6. **Function Overloading:**
   - C++ allows you to define multiple functions with the same name but different parameter lists. This is called function overloading.

     ```cpp
     int add(int a, int b);
     double add(double a, double b);
     ```

7. **Scope:**
   - Variables declared inside a function have local scope, meaning they are only accessible within that function.

8. **Main Function:**
   - The `main()` function is the entry point of C++ programs.

     ```cpp
     int main() {
         // program logic
         return 0;
     }
     ```
