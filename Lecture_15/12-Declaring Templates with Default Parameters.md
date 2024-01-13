[//]: # (### Declaring Templates with Default Parameters)

We can modify the previous version of `HoldsPair <...>` to declare `int` as the default template parameter type:

```cpp
template <typename T1=int, typename T2=int>
class HoldsPair 
{ 
    // ... method declarations 
}
```

 This is similar in construction to functions that define default input parameter values except for the fact that, in this case, you define default types. The use of `HoldsPair` can thus be compacted to

 ```cpp
// Pair an int with an int (default type) 
HoldsPair<> pairInts (6, 500);
 ```
