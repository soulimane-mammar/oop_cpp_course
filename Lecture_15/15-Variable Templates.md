[//]: # (### Variadic Templates)

Variadic templates in C++ are a powerful feature that allows you to define functions, classes, or structures that can accept a variable number of template arguments. This feature was introduced in C++11 and is particularly useful when you need to work with functions or classes that can handle an arbitrary number of arguments.

#### Example of a Variadic Function

```cpp
#include <iostream>

// Base case for recursion
void print() {
    std::cout << std::endl;
}

// Variadic template function for printing multiple arguments
template <typename T, typename... Args>
void print(T first, Args... args) {
    std::cout << first << ' ';
    print(args...);  // Recursive call with remaining arguments
}

int main() {
    print(1, 2.5, "Hello", 'A');

    return 0;
}
```

In this example:

- The base case `print()` does nothing and serves as the termination condition for recursion.
- The variadic template function `print` takes a first argument of type `T` and a variable number of additional arguments of types specified by `Args...`.
- Inside the function, the first argument is printed, and then the function is recursively called with the remaining arguments until the base case is reached.

#### Another Example of a Variadic Function

```cpp
#include <iostream>
using namespace std;

template <typename Res, typename ValType>
void Sum(Res& result, ValType& val)
{
   result = result + val;
}

template <typename Res, typename First, typename... Rest> 
void Sum(Res& result, First val1, Rest... numN)
{
   result = result + val1; // use sizeof...(numN) to find number of variadic parameters
   return Sum(result, numN ...);
}

int main()
{
   double dResult = 0;
   Sum (dResult, 3.14, 4.56, 1.1111);
   cout << "dResult = " << dResult << endl;

   string strResult;
   Sum (strResult, "Hello ", "World");
   cout << "strResult = " << strResult.c_str() << endl;

   return 0;
}
```

This example illustrates that the function `Sum()` that you defined using variable templates not only processed completely different argument types,  but also processed a varying number of arguments.

During compilation, the compiler actually creates code for the right kind of `Sum()` that to suit the call, and it does so recursively until all arguments have been processed

#### Example of a Variadic Class

```cpp
#include <iostream>

// Variadic template class for creating a tuple
template <typename... Args>
class Tuple;

// Base case for an empty tuple
template <>
class Tuple<> {};

// Recursive case for a non-empty tuple
template <typename First, typename... Rest>
class Tuple<First, Rest...> {
public:
    First value;
    Tuple<Rest...> rest;

    Tuple(First v, Rest... r) : value(v), rest(r...) {}
};

int main() {
    Tuple<int, double, char> myTuple(42, 3.14, 'A');
    
    std::cout << "Tuple values: " << myTuple.value << ", " << myTuple.rest.value << ", " << myTuple.rest.rest.value << std::endl;

    return 0;
}
```

In this example:

- The variadic class `Tuple` is defined to represent a tuple with elements of types specified by `Args...`.
- The base case `Tuple<>` represents an empty tuple.
- The recursive case `Tuple<First, Rest...>` represents a non-empty tuple with a first element of type `First` and a rest element of type `Tuple<Rest...>`.
- The constructor initializes the first value and recursively initializes the rest of the tuple.

**Note**
>You can use the operator `sizeof...()` to determine the number of template arguments passed in a call to a variable template.
>You must not confuse `sizeof...()` with `sizeof(Type)`. The latter returns the size of a type, while the former returns the number of template arguments sent to a variadic template.
