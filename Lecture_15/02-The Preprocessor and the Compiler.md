[//]: # (### The Preprocessor and the Compiler)

The C++ preprocessor is a part of the compiler that processes the source code before it gets compiled. It handles preprocessing directives, which are lines in the code that begin with the `#` symbol. These directives provide a way to manipulate the code before it is compiled, offering benefits such as conditional compilation, inclusion of other files, and definition of macros.

Here are some common preprocessor directives in C++:

- `#include`: This directive is used to include other files in the source code. It's commonly used to include header files.

- `#define`: This directive is used to define macros. A macro is essentially a piece of text that is replaced by the preprocessor before the code is compiled.

- `#undef`: This directive is used to undefine a macro that has already been defined.

- `#ifdef`, `#ifndef`, `#if`, `#elif`, `#else`, `#endif`: These directives are used for conditional compilation. They allow parts of the code to be compiled only if certain conditions are met.

- `#error`, `#warning`: These directives are used to halt the compilation process and produce an error or warning message.

- `#pragma`: This directive provides the compiler with specific instructions.

Here's an example of how these directives are used:

```cpp
#include <iostream>
// define a macro constant 
#define PI 3.14
#define ARRAY_LENGTH 25

// define a macro function 
#define SQUARE(x) ((x) * (x))


int main() {
   std::cout << "The value of PI is " << PI << std::endl;
   int numbers[ARRAY_LENGTH]; // array of 25 integers  
   const int twentyFive = SQUARE(5);
   return 0;
}
```

This lesson focuses on two types of preprocessor directives shown in the code snippet above: one using `#define` to define a constant and another using `#define` to define a macro function. The directives instruct the preprocessor to replace every instance of the macro (`ARRAY_LENGTH` or `SQUARE`) with the value it defines.

**Note**
>Macros execute text substitution. The preprocessor does nothing intelligent. It simply replaces the identifier with other text—without validating the replacement
