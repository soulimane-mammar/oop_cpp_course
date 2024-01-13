[//]: # (### Template Instantiation and Specialization)

A template class is just a blueprint and therefore doesn’t truly exist for the compiler before it has been used.

That is, a template  you define but don’t consume is code that is simply ignored.

However, you instantiate a template, like `HoldsPair`, by supplying template arguments like this:

```cpp
HoldsPair<int, double> pairIntDbl;
```

Here you are instructing the compiler to create a class for you by using the template and to instantiate it for the types specified as template arguments (`int` and `double` in this case).

Thus, in the case of templates, instantiation is the act or process of creating a specific type using one or more template arguments.

On the other hand, there may be situations that require you to explicitly define a (different) behavior of a template when instantiated with a specific type. In such cases, you specialize a template for that type.

A specialization of the template class `HoldsPair` when instantiated with template parameters of type `int` would look like this:

```cpp
template<> class HoldsPair<int, int> 
{ 
    // implementation code here 
};
```

Code that specializes a template must follow the template definition.

The following code is an example of template specialization

```cpp
#include <iostream>
using namespace std;

template <typename T1 = int, typename T2 = double>
class HoldsPair
{
private:
   T1 value1;
   T2 value2;
public:
   HoldsPair(const T1& val1, const T2& val2) // constructor
      : value1(val1), value2(val2) {}

   // Accessor functions
   const T1& GetFirstValue() const;
   const T2& GetSecondValue() const;
};

// specialization of HoldsPair for types int & int here
template<> class HoldsPair<int, int>
{
private:
   int value1;
   int value2;
   string strFun;
public:
   HoldsPair(const int& val1, const int& val2) // constructor
      : value1(val1), value2(val2) {}

   const int & GetFirstValue() const
   {
      cout << "Returning integer " << value1 << endl;
      return value1;
   }
};
   
int main()
{
   HoldsPair<int, int> pairIntInt(222, 333);
   pairIntInt.GetFirstValue();

   return 0;
}
```

Output

```
Returning integer 222
```

Note that the original template definition doesn’t even supply an implementation of the accessor functions `GetFirstValue()` and `GetSecondValue()`, and the program still compiles. This is because the compiler was only required to consider the template instantiation for <int, int>—for which you have supplied a specialized implementation that is complete enough. Thus, this sample not only demonstrates template specialization but also how template code is considered or even ignored by the compiler, depending on its use.
