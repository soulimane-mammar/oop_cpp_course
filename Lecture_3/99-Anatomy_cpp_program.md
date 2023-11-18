#### Introduction

C++ programs are organized into classes comprising member functions and member
variables. Most of this book is devoted to explaining these parts in depth, but to get a sense of how a program fits together, you must see a  complete working program. In this lesson, you learn

- The parts of a C++ program
- How the parts work together
- What a function is and what it does
- Basic input and output operations

#### Parts of the Hello World Program

Let's analyse your first C++ program in Lecture 2, “Getting Started"

```cpp
1: // Preprocessor directive that includes header iostream
2: #include <iostream>
3:
4: // Start of your program: function block main()
5: int main()
6: {
7:  /* Write to the console output i.e. screen */
8:    std::cout << “Hello World” << std::endl;
9:
10: // Return a value to the OS
11:   return 0;
12: }
```

This C++ program can be broadly classified into two parts: the preprocessor directives that start with a `#` and the main body of the program, which starts with int `main()`.

>Lines 1, 4, 7, and 10, which start with a // or with a /*, are called comments and are ignored by the compiler. Comments are used to explain the code and are for humans to read.

##### Preprocessor Directive `#include`

A preprocessor is a tool that runs before the actual compilation starts. Preprocessor directives  start with a pound sign `#`  In line 2 of the above program, `#include <filename>` tells the preprocessor to take the contents of the file (`iostream`, in this case) and include them at the
line where the directive is made. `iostream` is a standard header file that enables the usage of `std::cout` in line 8.

##### The Body of The Program: `main()`

Characterized by the function `main()`. The execution of a C++ program always starts here. It is a standardized convention that function `main()` is declared with an `int` return value

In many C++ applications, you find a variant of the `main()` function that looks like this:

```cpp
int main (int argc, char* argv[])
```

This variant allows the user to start the program with command-line  arguments, such as

```
program -DoSomethingSpecific
```

 In line 8 `std::cout` is used to output the string "Hello, World" to the console. The `<<` operator is used to stream the string into the `cout` object. `std::endl` is used to insert a newline character

>The actual text "Hello World", including the quotes, is called a string
literal.

##### Returning a Value

The `main()` function return an integer value to the OS, this value can be very useful as most OSes provide for an ability to query on the return value of an application that has terminated naturally.
In many cases, one application is launched by another, and the parent application (that launches) wants to know if the child application (that was launched) has completed its task successfully.
A programmer can use the return value of `main()` to convey a success or error state to the parent application.

>Programmers conventionally return 0 in the event of success or -1 in the event of an error. However, the return value is an integer, and a programmer has the flexibility to convey many different states of success or failure by using the available range of integer return values.

#### The Concept of Namespaces

The reason to use `std::cout` in the program, rather than just `cout`, stems from the fact that the artifact (`cout`) is within the standard (`std`) namespace.

Assume that `cout` exist in two locations known to the compiler. Which one should be invoke? This conflict will result in a compilation failure. Namespaces solve this problem by giving names to sections of code. In invoking std::cout, you are instructing the compiler to use the `cout` that is available in the `std` namespace.

In order to repeatedly add the `std` namespace specifier, the `using
namespace` declaration, as demonstrated in following listing, helps avoid this repetition.

```cpp
1: // Preprocessor directive
2: #include <iostream>
3:
4: // Start of your program
5: int main()
6: {
7:    // Tell the compiler what namespace to search in
8:    using namespace std;
9:
10:   /* Write to the screen using std::cout */
11:   cout << “Hello World” << endl;
12:
13:   // Return a value to the OS
14:   return 0;
15: }
```

A more restrictive variant of the above listing is shown in following listing, where we do not include a namespace in its entirety. We explicitly include the only artifacts that we wish to use.

```cpp
1: // Preprocessor directive
2: #include <iostream>
3:
4: // Start of your program
5: int main()
6: {
7:      using std::cout;
8:      using std::endl;
9:
10:     /* Write to the screen using std::cout */
11:     cout << “Hello World” << endl;
12:
13:     // Return a value to the OS
14:     return 0;
15: }
```

Using namespace `std` is different from using `std::cout` in that the former permits the use of all artifacts (`cout`, `cin`, etc.) in the `std` namespace without explicitly including the namespace qualifier`std::`. With the latter, only `std::cout` can benefit from the simplicity of not having to explicitly disambiguate the namespace.

#### Comments in C++ Code

Comments in C++ are used to provide explanatory notes within the source code. These comments are ignored by the compiler and are intended for human readers to better understand the code. There are two main types of comments in C++:

1. **Single-line comments:**
   - Denoted by `//`.
   - Anything following `//` on the same line is treated as a comment.

   ```cpp
   // This is a single-line comment
   int x = 10; // This is an inline comment
   ```

2. **Multi-line comments:**
   - Enclosed between `/*` and `*/`.
   - Can span multiple lines.

   ```cpp
   /*
   This is a multi-line comment
   It can span several lines
   */
   int y = 20;
   ```

Comments are useful for providing context, explanations, or reminders to yourself or others who might read the code. They contribute to code readability and can be crucial for understanding the purpose or functionality of specific code segments. However, it's important not to overuse comments or leave outdated comments, as they may lead to confusion. Well-written and concise comments enhance the maintainability and collaboration aspects of code.

#### Functions in C++

In C++, functions are blocks of code that perform a specific task. They are fundamental to structured programming and enable code reuse, modularity, and abstraction.

Here's a simple C++ program that includes the functions:

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

#### Basic Input Using `std::cin` and Output Using `std::cout`

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
