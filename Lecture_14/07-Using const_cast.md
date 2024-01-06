[//]: # (### Using const_cast)

`const_cast` is a type of casting operator in C++ that is used to cast away the `const`-ness of a variable or a pointer. This means it allows you to modify a `const` variable or a pointer to a `const` object [Source 1](https://www.geeksforgeeks.org/const_cast-in-c-type-casting-operators/).

The syntax of `const_cast` is as follows:

```cpp
const_cast<data_type>(expression)
```

Here's an example of how `const_cast` is used:

```cpp
const int x = 50;
const int* y = &x;
int* z = const_cast<int*>(y);
*z = 100;
```

In this example, a `const` integer `x` is initialized with the value 50. A `const` pointer `y` is then initialized to point to `x`. Finally, `const_cast` is used to create a non-`const` pointer `z` that points to `x`, allowing us to change the value of `x` through `z`.

While `const_cast` can be useful in certain scenarios, such as interfacing with legacy APIs that aren't `const`-correct, it should be used sparingly and with caution. Casting away `const`-ness can lead to undefined behavior if the original object was indeed `const`.

Moreover, `const_cast` can also be used to cast away the `volatile` attribute of a variable. However, just like with `const`, it should be used with care as it can lead to undefined behavior if the original object was `volatile`.
