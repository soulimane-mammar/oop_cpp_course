[//]: # (### Template Classes and static Members)

How would static member attributes function within a template class?

It’s similar with a template class, too, except for the fact that a static member is shared across all objects of a template class with the same template instantiation.

So a static member `X` within a template class is static within all instances of the class instantiated for `int`. Similarly, another instance of `X` is also static within all instances of the class specialized for `double`, independent of the other template instantiation for `int`.  

The following code demonstrates this concept.

```cpp
#include <iostream>
using namespace std;

template <typename T>
class TestStatic
{
public:
   static T staticVal;
};
   
// static member initialization
template<typename T> T TestStatic<T>::staticVal;

int main()
{
   TestStatic<int> intInstance;
   cout << "Setting staticVal for intInstance to 2024" << endl;
   intInstance.staticVal = 2024;

   TestStatic<double> dblnstance;
   cout << "Setting staticVal for dblnstance to 1011.022" << endl;
   dblnstance.staticVal = 1011.022;

   cout << "intInstance.staticVal = " << intInstance.staticVal << endl;
   cout << "dblnstance.staticVal = " << dblnstance.staticVal << endl;

   return 0;
}
```

Output

```
Setting staticVal for intInstance to 2024 
Setting staticVal for dblnstance to 1011.022 
intInstance.staticVal = 2024 
dblnstance.staticVal = 1011.02
```

**Note**
>Note the static member instantiation syntax for a template class
`template<typename T> T TestStatic<T>::staticVal;`
