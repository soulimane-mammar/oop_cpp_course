[//]: # (####The Concept of Namespaces)

The reason to use `std::cout` in the program, rather than just `cout`, stems from the fact that the artifact (`cout`) is within the standard (`std`) namespace.

Assume that `cout` exist in two locations known to the compiler. Which one should be invoked? This conflict will result in a compilation failure. Namespaces solve this problem by giving names to sections of code. In invoking `std::cout`, you are instructing the compiler to use the `cout` that is available in the `std` namespace.

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

A more restrictive variant of the above listing is shown in the following listing, where we do not include a namespace in its entirety. We explicitly include the only artifacts that we wish to use.

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

`using namespace std` is different from `using std::cout` in that the former permits the use of all artifacts (`cout`, `cin`, etc.) in the `std` namespace without explicitly including the namespace qualifier `std::`. With the latter, only `std::cout` can benefit from the simplicity of not having to explicitly disambiguate the namespace.
