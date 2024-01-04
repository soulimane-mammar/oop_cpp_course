[//]: # (### What Are Operators in C++)

There is very little that differentiates an operator from a function on a syntactical level, except for the use of the keyword `operator`.

An operator declaration looks quite like a function declaration:

```cpp
return_type operator operator_symbol (...parameter list...);
```

`operator_symbol` in this case could be any of the several operator types that a programmer can define: `+` (addition), `&&` (logical AND), and so on.

So, why does C++ provide operators when functions are also supported?
Consider a utility class `Date` that encapsulates the day, month, and year:

```cpp
Date independenceDay (07, 5, 1962); // initialized to Jul 5, 1962
```

If you want to add a day and get the instance to contain the next day—July 6, 1962— which of these two options would be more intuitive?

```cpp
++ independenceDay ; // Jul 6, 1962
```

or

```cpp
independenceDay.increment() ; // Jul 6, 1962
```

Clearly the first option is more convenient. The operator-based mechanism facilitates consumption by supplying ease of use and intuitiveness. Implementing the operator `<` in the class `Date` would help you compare two instances of the class `Date` like this:

```cpp
if(date1 < date2) 
{ 
    // Do something 
} 
else 
{ 
    // Do something else 
}
```

Operators can be used in more situations than just managing dates. They’re essential to classes such as `std::string` that provide string concatenation features. Smart pointer classes leverage the operators `->` and `*` in helping a programmer with pointer and memory management.
