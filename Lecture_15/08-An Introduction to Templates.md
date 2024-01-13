[//]: # (### An Introduction to Templates)

Templates are arguably one of the most powerful features of the C++.  A template in C++ enables you to define a behavior that you can apply to objects of varying types. This sounds ominously close to what macros let you do; think about the simple macro `MAX` that determined the greater of two numbers. However, macros are type unsafe, and templates are type safe.

#### Template Declaration Syntax

```cpp
template  <parameter list> 
function or class declaration
```

The keyword `template` marks the start of a template declaration, and the template parameter list contains the keyword `typename`, which defines the template parameter `objType`, making it a placeholder for the type of the object that the template is being instantiated for:

```cpp
template <typename T1, typename T2 = T1> 
bool TemplateFunction(const T1& param1, const T2& param2); 

// A template class 

template <typename T1, typename T2 = T1> 
class MyTemplate 
{ 
private: 
    T1 member1; 
    T2 member2;
public: 
    T1 GetMember1() 
    {
        return member1; 
    } 
    // ... other methods };
```

#### The Different Types of Template Declarations

A template declaration can be

- A declaration or definition of a function
- A declaration or definition of a class
- A definition of a member function or a member class of a class template
- A definition of a static data member of a class template
- A definition of a static data member of a class nested within a class template
- A definition of a member template of a class or class template
