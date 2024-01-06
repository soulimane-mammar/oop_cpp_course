[//]: # (### Why C-Style Casts Are Not Popular with Some C++ Programmers)

C-style casts are not type safe. They can hide conversion warnings and errors by silencing the compiler, which can lead to unexpected behavior or bugs. For example, most C++ compilers won’t let you get away with this:

```cpp
char*staticStr = “Hello World!”; 
int* intArray = staticStr; // error: cannot convert char*to int*
```

—and rightfully so! Having said that, compilers need to be backward compliant to support legacy code; therefore, they need to permit casting.

In doing so, they permit code such as:

```cpp
int*intArray = (int*)staticStr; // cast one problem away, create another
```

This C-style cast forces the compiler to interpret the destination as a type that the programmer wanted to assign to. The casting suppresses compile errors even though the types are totally incompatible. In this case, the programmer effectively muzzles the compiler and forces it to obey. In interpreting the `char*` as an `int*`, the compiler did not perform any conversion. In other words, in this example, a C-style cast compromised type safety and undermined the quality of the program.
