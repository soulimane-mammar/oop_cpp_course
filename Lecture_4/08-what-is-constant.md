[//]: # (###What Is a Constant?)

In programming, a constant is a value that cannot be altered or changed during the execution of a program. It's essentially a variable whose value remains fixed or constant throughout the program's execution.

#### Literal Constants

Literal constants refer to fixed values directly written into the code, maintaining their value throughout program execution. These constants are not variables.

##### Types of Literal Constants in C++

1. **Integer Constants**: Represent whole numbers without decimal points.

    ```cpp
    int number = 10; // Integer literal constant
    ```

2. **Floating-Point Constants**: Represent numbers with a decimal point.

    ```cpp
    double pi = 3.14; // Floating-point literal constant
    ```

3. **Character Constants**: Represent single characters enclosed in single quotes.

    ```cpp
    char letter = 'A'; // Character literal constant
    ```

4. **String Constants**: Represent sequences of characters enclosed in double quotes.

    ```cpp
    string text = "Hello, World!"; // String literal constant
    ```

5. **Boolean Constants**: Represent logical values, either `true` or `false`.

    ```cpp
    bool flag = true; // Boolean literal constant
    ```

6. **Null Pointer Constant**: Represent a null pointer value.

    ```cpp
    int* ptr = nullptr; // Null pointer literal constant
    ```

#### Declaring Variables as Constants Using `const`

In C++, the `const` keyword is used to declare constants, which are variables whose values cannot be changed once they are initialized.

```cpp
1: #include <iostream>
2:
3: int main()
4: {
5:   using namespace std;
6:
7:   const double pi = 22.0 / 7;
8:   cout << “The value of constant pi is: “ << pi << endl;
9:
10:  // Uncomment next line to fail compilation
11:  // pi = 345; // error, assignment to a constant
12:
13:  return 0;
14: }
```

Note the declaration of the constant pi in Line 7. You use the const keyword to tell the compiler that `pi` is a constant of type double. If you uncomment Line 11, which assigns a value to a constant, you get a compile failure that says something similar to, “You cannot assign to a variable that is `const`.” Thus, using constants is a powerful way to ensure that certain data cannot be modified.

#### Constant Expressions Using `constexpr`

In C++, `constexpr` is a keyword used to declare variables or functions as compile-time constants, allowing expressions to be evaluated at compile time.

##### Constants with `constexpr`

```cpp
constexpr int MAX_VALUE = 100;
```

Here, `MAX_VALUE` is a constant of type `int`, and it must be initialized with a value that the compiler can evaluate at compile time.

##### Functions with `constexpr`

```cpp
constexpr int square(int x) {
    return x * x;
}
```

This `square()` function is marked as `constexpr`, indicating that it can be evaluated at compile time if its arguments are constant expressions.

```cpp
constexpr int result = square(5); // Evaluated at compile time
int y = 7;
// constexpr int result2 = square(y); // Not allowed, y is not a constant expression
```

The usage of `constexpr` helps in ensuring that certain computations are performed at compile time, reducing runtime overhead and enabling more opportunities for optimization. However, there are limitations to what can be achieved with `constexpr`, and not all computations or functions can be made `constexpr`.

#### C++20 Immediate Functions Using `consteval`

In C++20, `consteval` is introduced to specify that a function must be evaluated at compile time, allowing computations to happen during compilation rather than at runtime. This can be particularly useful for performance-critical code or for ensuring certain operations are resolved at compile time.

Immediate functions, or functions marked with `consteval`, ensure that they're only called in constant expressions, such as template arguments, `constexpr` variables, and other contexts where values must be known at compile time.

Here's a simple example of using `consteval`:

```cpp
#include <iostream>

consteval int Square(int x) {
    return x * x;
}

int main() {
    constexpr int result = Square(5); // Compile-time computation
    std::cout << "Square of 5 is: " << result << std::endl;
    
    // Error: attempting to use Square in a non-constant expression
    int y = 10;
    // int result_runtime = Square(y); // This would not compile
    return 0;
}
```

In this example, `Square()` is marked as `consteval`, guaranteeing that it will be computed at compile time when invoked in a constant expression (`constexpr int result = Square(5)`). Trying to call `Square()` with a non-constant argument (e.g., `int result_runtime = Square(y);`) would result in a compilation error.

Immediate functions offer the advantage of catching errors at compile time if used incorrectly, providing a means to perform computations at compile time, and potentially enhancing performance by moving some calculations from runtime to compile time.

#### Enumerations

Enumerations (enums) in C++ are user-defined data types used to assign names to integral constants. They provide a way to create a set of named integer constants, making the code more readable, maintainable, and expressive.

Here's a basic example:

```cpp
#include <iostream>

enum Color {
    RED,
    GREEN,
    BLUE
};

int main() {
    Color c = RED;

    if (c == RED) {
        std::cout << "The color is red." << std::endl;
    } else if (c == GREEN) {
        std::cout << "The color is green." << std::endl;
    } else if (c == BLUE) {
        std::cout << "The color is blue." << std::endl;
    }

    return 0;
}
```

In this example, `Color` is an enumeration that defines three constants: `RED`, `GREEN`, and `BLUE`, which are implicitly assigned integer values starting from 0. By default, the first enumerator is assigned the value `0`, and subsequent enumerators are assigned values incremented by 1.

Enums can be explicitly assigned values:

```cpp
enum Direction {
    UP = 1,
    DOWN = -1,
    LEFT = 2,
    RIGHT = 3
};
```

Enums can also be scoped:

```cpp
enum class TrafficLight {
    RED,
    YELLOW,
    GREEN
};

int main() {
    TrafficLight light = TrafficLight::RED;

    if (light == TrafficLight::RED) {
        // Do something
    }

    return 0;
}
```

Enumerations help make code more readable and self-documenting, especially when dealing with sets of related constants. Additionally, enums can be very useful in switch statements, providing a clean and expressive way to handle different cases based on enum values.

The enumerated type `Color` is defined as an unscoped enumeration. The compiler lets you convert variables of this type into integers, and therefore the following statement would be valid:

```cpp
int someNumber = RED;
```

This flexibility, however, defeats the very purpose of using enumerations. You’re therefore advised to use scoped enumerations instead. Introduced in 2011 as part of C++11, scoped enumerations offer better scoping and type safety compared to traditional enums.
They are declared using the `enum class` syntax. Unlike traditional enums, scoped enums do not implicitly convert to integers or other enum types, offering stronger type checking and encapsulation.

Here's an example of using scoped enums:

```cpp
#include <iostream>

enum class TrafficLight {
    RED,
    YELLOW,
    GREEN
};

int main() {
    TrafficLight light = TrafficLight::RED;

    // Error: Cannot directly compare different enum types or with integers
    // if (light == 0) { /* ... */ } // This comparison won't compile

    if (light == TrafficLight::RED) {
        std::cout << "Stop!" << std::endl;
    } else if (light == TrafficLight::YELLOW) {
        std::cout << "Prepare to stop." << std::endl;
    } else if (light == TrafficLight::GREEN) {
        std::cout << "Go!" << std::endl;
    }

    return 0;
}
```

In this example, `TrafficLight` is a scoped enum, and its enumerators (`RED`, `YELLOW`, `GREEN`) are accessed using the scope resolution operator `::`. Scoped enums provide stronger type safety, preventing direct comparisons with integers or other unrelated enum types, reducing potential bugs and enhancing code readability.

Scoped enums also don't leak their enumerators into the surrounding scope. This means that you need to use the enum's scope (`TrafficLight::RED`, `TrafficLight::YELLOW`, etc.) to access the enumerators. It prevents naming collisions and keeps the enum values encapsulated within their namespace.

Scoped enums are preferable in many situations due to their better encapsulation, type safety, and avoidance of naming conflicts, especially in larger codebases where explicit scoping and type safety are crucial.

#### Defining Constants by Using `#define`

`#define` is a preprocessor directive used to define constants or macros. It's a simple text substitution mechanism that replaces occurrences of defined names with their values before the actual compilation of the code.

Here's an example of using `#define` to define constants:

```cpp
#include <iostream>

#define PI 3.14159
#define MAX_VALUE 100

int main() {
    double radius = 5.0;
    double area = PI * radius * radius;

    if (area > MAX_VALUE) {
        std::cout << "Area exceeds maximum value." << std::endl;
    }

    return 0;
}
```

In this example, `PI` and `MAX_VALUE` are defined using `#define`. During the preprocessing stage, the preprocessor replaces all occurrences of `PI` with `3.14159` and `MAX_VALUE` with `100` throughout the code before it's compiled.

However, there are some downsides to using `#define` for constants:

1. **No Type Safety:** `#define` creates literal text replacements, so there's no type checking. For example, `#define MAX_VALUE 100` won't prevent you from using `MAX_VALUE` as a string or any other type.

2. **Scope Issues:** Constants defined with `#define` are global and have no scope. They exist throughout the entire code, potentially leading to naming collisions or unexpected behavior.

3. **Debugging Difficulty:** Since `#define` is a text substitution mechanism, it might make debugging more challenging as the actual values may not be visible during debugging.

In modern C++, `const` or `constexpr` variables are often preferred over `#define` for defining constants. For instance:

```cpp
#include <iostream>

const double PI = 3.14159;
constexpr int MAX_VALUE = 100;

int main() {
    double radius = 5.0;
    double area = PI * radius * radius;

    if (area > MAX_VALUE) {
        std::cout << "Area exceeds maximum value." << std::endl;
    }

    return 0;
}
```

Using `const` or `constexpr` variables instead of `#define` offers type safety, scope control, and better debugging support, making the code more maintainable and less error-prone.
