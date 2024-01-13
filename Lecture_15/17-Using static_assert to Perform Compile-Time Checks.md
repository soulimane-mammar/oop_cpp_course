[//]: # (### Using static_assert to Perform Compile-Time Checks)

`static_assert` is a C++11 feature that allows you to perform compile-time assertions. It provides a mechanism to check conditions at compile time and generate a compilation error if the specified condition is not met. This helps catch errors early in the development process.

#### Syntax

```cpp
static_assert(condition, message);
```

- `condition`: The compile-time condition that must be true.
- `message`: A string literal or an identifier that serves as a custom error message if the condition is not met.

#### Compile-Time Checking Example 1

```cpp
#include <iostream>

template <typename T>
class MyClass {
    static_assert(std::is_integral<T>::value, "Template type must be integral.");
public:
    T value;
    MyClass(T val) : value(val) {}
};

int main() {
    // Compile-time error: MyClass<double> does not satisfy the static_assert condition
    // MyClass<double> obj(3.14); 

    // Compile-time success: MyClass<int> satisfies the static_assert condition
    MyClass<int> obj(42);

    return 0;
}
```

In this example:

- The `static_assert` statement is used inside the template class `MyClass` to ensure that the template type `T` is integral using `std::is_integral`.
- If the condition is not met (e.g., if someone tries to instantiate `MyClass<double>`), a compilation error will occur, and the specified error message will be displayed.

#### Key Points

- `static_assert` conditions are evaluated at compile time, and the error message is generated during the compilation process.
- It is commonly used for template metaprogramming to enforce constraints on template parameters.
- The condition must be a constant expression that can be evaluated at compile time.

#### Compile-Time Checking Example 2

```cpp
template <typename T, typename U>
T add(T a, U b) {
    static_assert(std::is_same_v<T, U>, "Types must be the same for add function.");
    return a + b;
}

int main() {
    // Compile-time error: add function expects the same types
    // int result = add(3, 4.5);

    // Compile-time success: add function called with the same types
    int result = add(3, 4);

    return 0;
}
```

Here, `static_assert` is used to ensure that the types passed to the `add` function are the same, providing a compile-time check for type safety.
