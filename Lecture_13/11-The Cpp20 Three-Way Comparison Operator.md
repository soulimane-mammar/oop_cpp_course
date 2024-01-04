[//]:# (### The C++20 Three-Way Comparison Operator <=>)

This operator was first introduced in lesson 6. The following code  shows how to define a `<=>` operator—which is informally called a spaceship operator because of its shape—for the class Date.

```cpp
#include <iostream>
#include <compare>
using namespace std;

class Date
{
private:
   int day, month, year;

public:
   Date(int inMonth, int inDay, int inYear)
      : month(inMonth), day(inDay), year(inYear) {}

   auto operator <=>(const Date& rhs) const
   {
      if (year < rhs.year)
         return std::strong_ordering::less;
      else if (year > rhs.year)
         return std::strong_ordering::greater;
      else
      {
         // years are identical, compare months
         if (month < rhs.month)
            return std::strong_ordering::less;
         else if (month > rhs.month)
            return std::strong_ordering::greater;
         else
         {
            // months are identical, compare days
            if (day < rhs.day)
               return std::strong_ordering::less;
            else if (day > rhs.day)
               return std::strong_ordering::greater;
            else
               return std::strong_ordering::equal;
         }
      }
   }
};

int main()
{
   cout << "Enter a date: month, day & year" << endl;
   int month, day, year;
   cin >> month;
   cin >> day;
   cin >> year;
   Date date1(month, day, year);

   cout << "Enter another date: month, day & year" << endl;
   cin >> month;
   cin >> day;
   cin >> year;
   Date date2(month, day, year);

   auto result = date1 <=> date2;

   if (result < 0)
      cout << "Date 1 occurs before Date 2" << endl;
   else if (result > 0)
      cout << "Date 1 occurs after Date 2" << endl;
   else
      cout << "Dates are equal" << endl;

   return 0;
}
```

Output

First run

```
Enter a date: month, day & year
7
25
2024
Enter another date: month, day & year
1
1
2025
Date 1 occurs before Date 2

```

Second run

```
Enter a date: month, day & year
6
2
2030
Enter another date: month, day & year
1
1
2001
Date 1 occurs after Date 2

```

Third run

```
Enter a date: month, day & year
7
24
2024
Enter another date: month, day & year
7
24
2024
Dates are equal
```
