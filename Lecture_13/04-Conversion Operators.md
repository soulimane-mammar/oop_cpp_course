[//]: # (### Conversion Operators)

Let's consider the last example and say that want to insert the following line in `main()`:

```cpp
cout << independenceDay; // error in absence of conversion operator
```

The code would result in the following compile error:

```
error: binary ’<<’ : no operator found which takes a right-hand operand of type ’Date’ (or there is no acceptable conversion).
```

This error essentially indicates that `cout` doesn’t know how to interpret an instance of `Date` because the `Date` class does not support the operators that convert its contents into a type that `cout` would accept.

`cout` can work well with a `const char*`:

```cpp
std::cout << “Hello world”; // const char* works!
```

Making `cout` compatible with a `Date` instance could be achieved by introducing an operator that returns a `const char*` representation of that instance,

```cpp
operator const char*() 
{ 
    // operator implementation that returns a char*
}
```

#### Example

```cpp
#include <iostream>
#include <sstream> // new include for ostringstream
#include <string>
using namespace std;

class Date
{
private:
   int day, month, year;
   string dateInString;

public:
   Date(int inMonth, int inDay, int inYear)
      : month(inMonth), day(inDay), year(inYear) {};

   operator const char*()
   {
      ostringstream formattedDate; // assists string construction
      formattedDate << month << " / " << day << " / " << year;
     
      dateInString = formattedDate.str();
      return dateInString.c_str();
   }
};
   
int main ()
{
   Date independenceDay(7, 5, 1962);

   cout << "Independence is on: " << independenceDay << endl;

   // string strHolyday (independenceDay); // OK!
   // strHolyday = Date(11, 1, 2023); // also OK!

   return 0;
}
```

Output

```
Independence is on: 7 / 5/ 1962
```

In this program we use `std::ostringstream` to convert the member integers into a `std::string` object. We could instead directly return `formattedDate.str()`, but we store a copy in the private member `Date::dateInString` because `formattedDate`, as a local variable, is destroyed when the operator returns. So, the pointer returned by `formattedDate.c_str()` would be invalidated on function return. `std::string::c_str()`  returns the C-style `const char*` equivalent of the contents in the string object.

The `const char*` operator  allows you to even assign an instance of the `Date` class directly to a string:

```cpp
string strHolyday (independenceDay); 
strHolyday = Date(11, 1, 2023); 
```

>**Caution**
>Note that such assignments cause implicit conversions. That is, the compiler uses the available conversion operator (in this case, `const char*`), thereby permitting unintended assignments that be compiled without errors. To avoid implicit conversions, use the keyword `explicit` at the beginning of an operator declaration, as follows:

```cpp
explicit operator const char*() 
{ 
    // conversion code here 
}
```

Using explicit would force a programmer to assert the intention to convert using a cast:

```cpp
string strHoliday(static_cast<const char*>(holiday));
strHoliday=static_cast<const char*>(Date(11,1,2023));
```
