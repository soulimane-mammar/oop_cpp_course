[//]: # (### The Function Operator )

The operator `()`, which makes objects behave like functions, is called a function operator.

Such function objects are typically called unary or binary predicates, depending on the number of operands they work on.

The following code shows a really simple function object.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Display
{
public:
   void operator () (string input) const
   {
      cout << input << endl;
   }
};

int main ()
{
   Display displayFuncObj;

   // equivalent to displayFuncObj.operator () ("Display this string!");
   displayFuncObj ("Display this string!"); 

   return 0;
}
```

Output

```
Display this string!
```
