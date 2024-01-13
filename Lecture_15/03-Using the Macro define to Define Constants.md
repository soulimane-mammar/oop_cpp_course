[//]: # (### Using the Macro #define to Define Constants)

The syntax you use with `#define` to compose a constant is simple:

```cpp
#define identifier replacement-text 
```

For example, you define the constant `ARRAY_LENGTH` to be substituted with `25` as follows:

```cpp
#define ARRAY_LENGTH 25
```

This identifier is now replaced by `25` wherever the preprocessor encounters the text `ARRAY_LENGTH`:

```cpp
int numbers[ARRAY_LENGTH]; 
double radiuses[ARRAY_LENGTH]; 
std::string names[ARRAY_LENGTH];
```

After the preprocessor runs, the code above is visible to the compiler as follows:

```cpp
int numbers[25]; // an array of 25 integers 
double radiuses[25]; // an array of 25 doubles 
std::string names[25];// an array of 25 std::strings
```

The replacement is applicable to every section of your code, including a for loop such as this one:

```cpp
for(int index = 0; index < ARRAY_LENGTH; ++index) 
    numbers[index] = index;
```

This for loop is visible to the compiler as

```cpp
for(int index = 0; index < 25; ++index) 
    numbers[index] = index;
```

To see exactly how such a macro works, review the following code.

```cpp
#include <iostream>
#include<string>
using namespace std;

#define ARRAY_LENGTH 25
#define PI 3.1416
#define MY_DOUBLE double
#define FAV_DRINK "Water"

/*
// Superior alternatives (comment those above when you uncomment these)
const int ARRAY_LENGTH = 25;
const double PI = 3.1416;
typedef double MY_DOUBLE;
const char* FAV_DRINK = "Water";
*/

int main()
{
   int MyNumbers [ARRAY_LENGTH] = {0};
   cout << "Array's length: " << sizeof(MyNumbers) / sizeof(int) << endl;

   cout << "Enter a radius: ";
   MY_DOUBLE Radius = 0;
   cin >> Radius;
   cout << "Area is: " << PI * Radius * Radius << endl;

   string FavoriteDrink (FAV_DRINK);
   cout << "My favorite drink is: " << FAV_DRINK << endl;

   return 0;
}
```

Output

```
Array’s length: 25 
Enter a radius: 2.1569 
Area is: 14.6154 
My favorite drink is: Water

```

**Tip**

In executing text substitutions, the preprocessor does not check for the correctness of the substitution (but the compiler always does). You could define FAV_DRINK like this:

```cpp
# define FAV_DRINK 42 // previously "Water"
```

 This would result in a compilation error for the `std::string` instantiation. However, in the absence this line, the compiler would go ahead and print the following:

```
 My favorite drink is: 42
```

This, of course, wouldn’t make sense, and, most importantly, it would go through undetected. In addition, you wouldn’t have much control over the macro-defined constant `PI`: Is it a `double` or a `float`? The answer is neither. To the preprocessor, `PI` is just a text substitution element `3.1416`. It is not a defined data type.

Constants are best defined using the `const` keyword with data types instead. Here is a superior alternative:

```cpp
const int ARRAY_LENGTH = 25; 
const double PI = 3.1416; 
const char* FAV_DRINK = "Water"; 
typedef double MY_DOUBLE; // typedef aliases a type

```
