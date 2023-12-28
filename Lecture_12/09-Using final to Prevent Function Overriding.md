[//]: # (### Using final to Prevent Function Overriding)

The specifier `final` was first presented to you in Lesson 10. A class declared as `final` cannot be used as a base class. Similarly, a virtual function declared as `final` cannot be overridden in a derived class.

Thus, a version of the class Tuna that doesn’t allow any further specialization of the virtual function `Swim()` would look like this:

```cpp
class Tuna:public Fish 
{ 
public: 
    // override Fish::Swim and make this final 
    void Swim() override final 
    { 
        cout << “Tuna swims!” << endl; 
    } 
};
```

This version of `Tuna` can be inherited from, but `Swim()` cannot be overridden any further:

```cpp
class BluefinTuna final:public Tuna 
{ 
public: 
    void Swim() // Error: Swim() was final in Tuna, cannot override 
    { 
    } 
};
```
