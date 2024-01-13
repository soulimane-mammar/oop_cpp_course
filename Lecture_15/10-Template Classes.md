[//]: # (### Template Classes)

Template classes are templatized versions of C++ classes; they are blueprints of blueprints. When using a template class, you are given the option to specify the "type" you are specializing the class for.

A simple template class that uses a single template parameter `T` to hold a member variable of type `T` can be defined as follows:

```cpp
template <typename T> 
class HoldVarTypeT 
{ 
private: 
    T value; 
public: 
    void SetValue (const T& newValue) 
    { 
        value = newValue;
    } 
    T& GetValue() 
    {
        return value;
    } 
};
```

The type of the variable value is T, and T is resolved at the time the template is used—that is, when the template is *instantiated*. So, let’s look at a sample usage of this template class:

```cpp
HoldVarTypeT<int> holdInt; // template instantiation for int 
holdInt.SetValue(5); 
cout << "The value stored is: "  << holdInt.GetValue() << endl;
```

This example shows how to use this template class to hold and retrieve an object of type `int`; that is, the Template class is instantiated for a template parameter of type `int`. Similarly, you can use the same class to deal with strings in a similar manner:

```cpp
HoldVarTypeT<string> holdStr; 
holdStr.SetValue("Sample string"); 
cout << "The value stored is: " << holdStr.GetValue() << endl;
```
