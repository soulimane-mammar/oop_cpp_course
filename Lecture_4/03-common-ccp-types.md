[//]: # (###Common Compiler-Supported C++ Variable Types)

In C++, there are several common variable types supported by compilers. These types determine the kind of data a variable can hold and the memory space it requires. Some of the widely used variable types include:

### Integer Types

- **int**: Used to store integers (whole numbers) such as -1, 0, 1, 100, etc. The size of `int` depends on the compiler but typically is at least 16 bits (usually 32 bits).
- **short**: Typically a smaller integer type, often at least 16 bits.
- **long**: Typically a larger integer type, often at least 32 bits (usually 64 bits).
- **long long**: Provides even larger storage for integers, often at least 64 bits. Introduced in C++11.
- **unsigned variants**: For non-negative integers, these types use their full range for positive values (e.g., `unsigned int`, `unsigned long`).

### Floating-Point Types

- **float**: Used to store floating-point numbers (real numbers) with single precision. Typically 32 bits.
- **double**: Used for double-precision floating-point numbers. Provides greater precision than `float`. Typically 64 bits.
- **long double**: Provides extended precision, larger than `double`. The size can vary among different compilers.

### Character Types

- **char**: Stores a single character, typically one byte in size. It can represent ASCII characters (e.g., 'a', 'A', '1', '$').
- **wchar_t**: Wide character type, used for handling wider character sets like Unicode. Platform-dependent size.

### Boolean Type

- **bool**: Represents boolean values `true` or `false`. Typically 1 byte in size.

### Void Type

- **void**: Indicates the absence of a type. Used in functions that don’t return a value (`void` functions) or with pointers to unspecified types (`void*`).

### Other Types

- **Enumerations (enums)**: User-defined types with a set of named constants.
- **User-defined types (classes/structs)**: Custom-defined data types that encapsulate data and behavior.

These variable types have specific ranges and memory requirements, which can vary based on the compiler and platform. Understanding these types and their characteristics is crucial for efficient memory usage and proper representation of data in C++ programs.
