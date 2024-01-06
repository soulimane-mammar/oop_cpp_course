[//]: # (### The Need for Casting)

A perfectly type-safe and type-strong world of well-written C++ applications has no need for casting or for casting operators.

However, we live in a world where modules may be programmed by different people who used different environments. Newly programmed code is required to work with legacy code and libraries.

To make this interoperability possible, compilers need to be instructed to interpret data in ways that make the application compile and function correctly. This interoperability is achieved using casting operators.

Let’s take a real-world example. C++ compilers support `bool` as a native type, and they need to support linking to libraries that were programmed years ago in C. Such legacy code and libraries often used an integer type to hold Boolean data because type bool wasn’t supported natively by the compiler back then.

A Boolean type back in the day was something akin to

```cpp
typedef unsigned short BOOL;
```

 A function that returns Boolean data would be declared as

 ```cpp
 BOOL IsX ();
 ```

The programmer of a new C++ application consuming a legacy library needs to make the `bool` data type that is supported natively by his compiler function with the `BOOL` data type that is returned by the library. The way to make this interoperability work is by using casts:

```cpp
bool Result = (bool)IsX(); // C-style cast interprets BOOL as bool
```

The evolution of C++ resulted in the emergence of C++ casting operators and continued support for the legacy C-style casting operator. You need to understand both casting styles because the world today uses both.
