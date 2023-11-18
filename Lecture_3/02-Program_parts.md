[//]: # (####Parts of the Hello World Program)

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

A preprocessor is a tool that runs before the actual compilation starts. Preprocessor directives  start with a pound sign `#`.  In line 2 of the above program, `#include <filename>` tells the preprocessor to take the contents of the file (`iostream`, in this case) and include them at the line where the directive is made. `iostream` is a standard header file that enables the usage of `std::cout` in line 8.

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

>The actual text "Hello World", including the quotes, is called a string literal.

##### Returning a Value

The `main()` function return an integer value to the OS, this value can be very useful as most OSes provide for an ability to query on the return value of an application that has terminated naturally.
In many cases, one application is launched by another, and the parent application (that launches) wants to know if the child application (that was launched) has completed its task successfully.
A programmer can use the return value of `main()` to convey a success or error state to the parent application.

>Programmers conventionally return 0 in the event of success or -1 in the event of an error. However, the return value is an integer, and a programmer has the flexibility to convey many different states of success or failure by using the available range of integer return values.
