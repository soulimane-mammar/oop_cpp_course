[//]: # (### Declaring Templates with Multiple Parameters)

You can expand the template parameter list to declare multiple parameters, separated by commas. So, if you want to declare a generic class that holds a pair of objects that can be of different types, you can do so by using the construct shown in the following example (which displays a template class with two template parameters):

```cpp
template <typename T1, typename T2> 
class HoldsPair 
{ 
private: 
    T1 value1; 
    T2 value2; 
public: 
    // Constructor that initializes member variables 
    HoldsPair (const T1& val1, const T2& val2) 
    { 
        value1 = val1; 
        value2 = val2; 
    };
    // ... Other member functions };
```

In this example, the class `HoldsPair` accepts two template parameters named `T1` and `T2`. You can use this class to hold two objects of the same type or of different types, as in:

```cpp
// A template instantiation that pairs an int with a double
HoldsPair<int, double> pairIntDouble(6, 1.99); 
// A template instantiation that pairs an int with an int
HoldsPair<int, int> pairIntDouble(6, 500);
```
