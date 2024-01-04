[//]: # (### The Equality == and Inequality != Operators)

What would you expect when one instance of the class `Date` is compared to another?

```cpp
if (date1 == date2) 
{ 
    // Do something 
} 
else 
{ 
    // Do something else 
}
```

In the absence of an equality operator (`==`), the compiler simply performs a binary comparison of the two objects and returns `true` when they are exactly identical.

This binary comparison will work for instances of classes containing simple data types (like the `Date` class as of now), but it will not work if the class in question has a non-static pointer member, such as the `int*` as the comparison of the member attributes would actually compare the member pointer values. The two pointers being compared would never be equal.

A generic expression of the equality operator is as follows:

```cpp
bool operator== (const ClassType& compareTo) 
{ 
    // comparison code here, return true if equal else false 
}
```

The inequality operator can reuse the equality operator:

```cpp
bool operator!= (const ClassType& compareTo) 
{ 
    // comparison code here, return true if inequal else false 
}
```

The following code demonstrates comparison operators defined by the calendar class `Date`.

```cpp
#include <iostream>
using namespace std;

class Date
{
private:
   int day, month, year;

public:
   Date(int inMonth, int inDay, int inYear)
      : month(inMonth), day(inDay), year(inYear) {}

   bool operator== (const Date& compareTo) const
   {
      return ((day == compareTo.day) 
            && (month == compareTo.month) 
           && (year == compareTo.year));
   }

   bool operator!= (const Date& compareTo) const
   {
      return !(operator==(compareTo));
   }

   void DisplayDate()
   {
      cout << month << " / " << day << " / " << year << endl;
   }
};
   
int main()
{
   Date holiday1 (7, 5, 2024);
   Date holiday2 (7, 30, 2024);

   cout << "holiday 1 is: ";
   holiday1.DisplayDate();
   cout << "holiday 2 is: ";
   holiday2.DisplayDate();

   if (holiday1 == holiday2)
      cout << "Equality operator: The two are on the same day" << endl;
   else
      cout << "Equality operator: The two are on different days" << endl;

   if (holiday1 != holiday2)
      cout << "Inequality operator: The two are on different days" << endl;
   else
      cout << "Inequality operator: The two are on the same day" << endl;

   return 0;
}
```

Output

```
holiday 1 is: 7 / 5 / 2024 
holiday 2 is: 7 / 30 / 2024 
Equality operator: The two are on different days 
Inequality operator: The two are on different days
```
