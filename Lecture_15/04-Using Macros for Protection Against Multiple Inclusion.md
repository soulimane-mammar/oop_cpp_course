[//]: # (### Using Macros for Protection Against Multiple Inclusion)

C++ programmers typically declare their classes and functions in `.h` files, also called header files. Functions are defined in `.cpp` files that include the header files using the `#include<header>` preprocessor directive.

If one header file—let’s call it `class1.h`— declares a class that has another class declared in `class2.h` as a member, then `class1.h` needs to include `class2.h`. If the design were complicated, and the other class required the former as well, then `class2.h` would include `class1.h`, too! For the preprocessor, however, two header files that include each other is a problem that is recursive in nature. Another problem arise when `class1.h`  includes `class2.h` and `class3.h` not knowing that `class2.h` also includes `class3.h` and end up including `class3.h` twice.

Using macros for protection against multiple inclusion, also known as header guards, is a common practice in C++ to avoid potential problems caused by multiple/recursive inclusions of header files. These problems could lead to issues such as redefinition errors, inconsistent data types, and unexpected behavior.

A typical header guard uses `#ifndef`, `#define`, and `#endif` preprocessor directives to ensure that the contents of the header file are only processed once. Here's a basic example:

```cpp
#ifndef HEADER_FILE_H
#define HEADER_FILE_H

// Contents of the header file go here...

#endif // HEADER_FILE_H
```

In this example, `HEADER_FILE_H` is a unique identifier for the header file. The first time this file is included, `HEADER_FILE_H` is not defined, so the preprocessor skips over the `#ifndef` directive and processes the entire file. The `#define` directive then defines `HEADER_FILE_H`, so if the file is included again, the `#ifndef` directive evaluates to false, and the preprocessor skips over the entire file.

**Note**
>`#ifndef` can be read as “if-not-defined.” It is a conditional processing command that instructs the preprocessor to continue only if the identifier has not been defined. This check ensures that the preprocessor works on the lines that follow only once.
`#endif` marks the end of this conditional processing instruction for the preprocessor.

**Tip**

`C++20` introduces modules. Modules provide a modern way of reusing code that was previously contained in header (`.h`) files. Modules don’t need multiple inclusion guards and drastically reduce the time required for compilation of particularly large code bases.
