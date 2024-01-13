[//]: # (### Advantages and Disadvantages of Using Macro Functions)

Macros enable you to reuse certain utility functions, regardless of the type of variables you are dealing with. Once again consider the following line of code:

```cpp
#define MIN(a, b) (((a) < (b)) ? (a) : (b))
```

 You can use this macro function `MIN` on integers:

 ```cpp
 cout << MIN(25, 101) << endl;
 ```

 But you can reuse it on double, too:

 ```cpp
cout << MIN(0.1, 0.2) << endl;
 ```

Note that if `MIN()` were a normal function, you would program two variants of it: `MIN_INT()`, which accepted `int` parameters and returned an `int`, and `MIN_DOUBLE()`, which does the same with type `double` instead.

These macro functions are expanded inline before compilation, and hence the performance of a simple macro is superior to that of an ordinary function call doing the same task. This is because the function call requires the creation of a call stack, passing arguments, and so on— administrative overload that often takes more CPU time than the calculation of `MIN` itself.

However, macros do not support any form of type safety, which compromises program quality and is a major disadvantage. In addition, debugging a complicated macro is not easy.

If you need the ability to program generic functions that are type independent yet type safe, use ***template functions*** instead. These functions are explained in the next section.
