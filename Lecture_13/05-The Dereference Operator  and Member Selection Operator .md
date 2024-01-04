[//]: # (### The Dereference Operator * and Member Selection Operator ->)

The dereference operator (`*`) and member selection operator (`->`) are most frequently used in smart pointer classes. Smart pointers are utility classes that wrap regular pointers and simplify memory management by resolving ownership and copy issues.

Analyze the use of `std::unique_ptr` in following program and observe how it uses the operators `*` and `->` to help you use the smart pointer class as you would any normal pointer.

```cpp
#include <iostream>
#include <memory>  // new include to use unique_ptr
using namespace std;

class Date
{
private:
   int day, month, year;
   string dateInString;   

public:
   Date(int inMonth, int inDay, int inYear)
      : month(inMonth), day(inDay), year(inYear) {};

   void DisplayDate()
   {
      cout << month << " / " << day << " / " << year << endl;
   }
};

int main()
{
   unique_ptr<int> smartIntPtr(new int);
   *smartIntPtr = 42;

   // Use smart pointer type like an int*
   cout << "Integer value is: " << *smartIntPtr << endl;

   unique_ptr<Date> smartHoliday (new Date(7, 5, 1962));
   cout << "The new instance of date contains: ";

   // use smartHoliday just as you would a Date*
   smartHoliday->DisplayDate();

   return 0; // smart pointers do the deallocation for you
}
```

Output

```
Integer value is: 42 
The new instance of date contains: 7 / 5 / 1962
```

This example demonstrates how a smart pointer allows you to use normal pointer syntax. You display the value of the `int` using `*smartIntPtr`, and you use `smartHoliday->DisplayData()` as if these two variables were an `int*` and a `Date*`, respectively. The secret lies in the implementation of operators`*` and `->` in the pointer class `std::unique_ptr`.
