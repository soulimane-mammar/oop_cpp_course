[//]: # (### Using #define to Write Macro Functions)

A preprocessor can simply replace text elements identified by a macro, and so a preprocessor is often used to write simple functions, as in this example:

```cpp
#define SQUARE(x) ((x) * (x))
```

This code determines the square of a number. Similarly, a macro that calculates the area of a circle looks like this:

```cpp
#define PI 3.1416 #define AREA_CIRCLE(r) (PI*(r)*(r))
```

Macro functions are often used for very simple calculations such as these. They appear like regular function calls, but they are expanded inline before compilation. They can therefore help improve code performance in certain cases. The following code demonstrates the use of these macro functions.

```cpp
#include <iostream>
#include<string>
using namespace std;

#define SQUARE(x) ((x) * (x))
#define PI 3.1416
#define AREA_CIRCLE(r) (PI*(r)*(r))
// #define AREA_CIRCLE(r) (PI*r*r) // uncomment this to understand why brackets are important (comment previous line)
#define MAX(a, b) (((a) > (b)) ? (a) : (b))
#define MIN(a, b) (((a) < (b)) ? (a) : (b))

int main()
{
   cout << "Enter an integer: ";
   int num1 = 0;
   cin >> num1;

   cout << "SQUARE(" << num1 << ") = " << SQUARE(num1) << endl;
   cout << "Area of a circle with radius " << num1 << " is: ";
   cout << AREA_CIRCLE(num1) << endl;

   cout << "Enter another integer: ";
   int num2 = 0;
   cin >> num2;

   cout << "MIN(" << num1 << ", " << num2 << ") = ";
   cout << MIN (num1, num2) << endl;

   cout << "MAX(" << num1 << ", " << num2 << ") = ";
   cout << MAX (num1, num2) << endl;

   return 0;
}
```

Output

```
Enter an integer: 36 
SQUARE(36) = 1296 
Area of a circle with radius 36 is: 4071.51 
Enter another integer: -101 
MIN(36, -101) = -101 
MAX(36, -101) = 36
```

#### Why All the Parentheses?

So, why do you use so many parentheses for the macro but not for the same formula in a function? The reason lies in the way the macro is evaluated: as a text substitution mechanism supported by the preprocessor.

Consider the macro without most of the brackets:

```cpp
#define AREA_CIRCLE(r) (PI*r*r)
```

What happens when you invoke this macro using a statement like this:

```cpp
cout << AREA_CIRCLE (4+6);
```

The compiler would expand it into

```cpp
cout << (PI*4+6*4+6); // not the same as PI*10*10
```

Thus, following the rules of operator precedence where multiplication happens before addition, the compiler actually evaluates the area like this:

```cpp
cout << (PI*4+24+6); // 42.5664 (which is incorrect)
```

Parentheses help avoid this problem:

```cpp
# define AREA_CIRCLE(r) (PI*(r)*(r))
cout << AREA_CIRCLE (4+6);
```

 The compiler views the expression after substitution as follows:

 ```cpp
 cout << (PI*(4+6)*(4+6)); // PI*10*10, as expected
 ```

The parentheses automatically result in the calculation of an accurate area, making your macro code independent of operator precedence and its effects.
