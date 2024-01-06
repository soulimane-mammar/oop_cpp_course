[//]: # (### Using static_cast)

`static_cast` can be used to convert pointers between related types and perform explicit type conversions for standard data types that would otherwise happen automatically or implicitly.

`static_cast` implements a basic compile-time check to ensure that a pointer is being cast to a related type. This is an improvement over a C-style cast, which allows a pointer to one object to be cast to an absolutely unrelated type without any complaint.

With `static_cast`, a pointer can be upcasted to the base type or can be downcasted to the derived type, as the following code sample indicates:

```cpp
Base* objBase = new Derived(); Derived* objDer = static_cast<Derived*>(objBase); // ok! 
// class Unrelated is not related to Base 
Unrelated* notRelated = static_cast<Unrelated*>(objBase); // Error 
// The cast is not permitted as types are unrelated
```

**Note**
>Casting `Derived*` to `Base*` is called *upcasting* and can be done without any explicit casting operator:

```cpp
Derived objDerived; 
Base* objBase = &objDerived; // ok!
```

>Casting `Base*` to `Derived*` is called *downcasting* and cannot be done without the use of explicit casting operators:

```cpp
Derived objDerived; 
Base* objBase = &objDerived; // Upcast, ok! 
Derived* objDer = objBase; // Error: Downcast, needs explicit casting
```

However, note that `static_cast` verifies only that the pointer types are related. It does not perform any runtime checks. So, with `static_cast`, a programmer could still get away with this bug:

```cpp
Base* objBase = new Base(); 
Derived* objDer = static_cast<Derived*>(objBase); // Still no errors!
```

Here, `objDer` points to a `Base` type but not to type `Derived`. `static_cast` performs a compile-time check by verifying that the types in question are related—which they are—and it therefore permits the casting.It does not perform a runtime check to ensure that the object being pointed to is of type Derived. Using this pointer `objDer` to call a method in the derived class `objDer->DerivedFunction()` would compile, but it would certainly result in unexpected behavior at execution.

In addition to helping in upcasting or downcasting, `static_cast` can, in many cases, help make implicit casts explicit and bring them to the attention of a programmer or reader:

```cpp
double Pi = 3.14159265; 
int num = static_cast<int>(Pi); // Making an otherwise implicit cast, explicit
```
