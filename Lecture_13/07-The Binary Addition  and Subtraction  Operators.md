[//]: # (### The Binary Addition (a+b) and Subtraction (a-b) Operators)

In the calendar `Date` class, although we have implemented the capability to increment `Date` so that it moves the calendar one day forward, we still do not support the capability to move it, say, five days ahead. To do this, you need to implement the binary operator (`+`), as in the following  code.

```cpp
#include <iostream>
using namespace std;
   
class Date
{
private:
   int day, month, year;
   string dateInString;

public:
   Date(int inMonth, int inDay, int inYear)
      : month(inMonth), day(inDay), year(inYear) {};
   
   Date operator + (int daysToAdd) // binary addition
   {
      Date newDate (month, day + daysToAdd, year);
      return newDate;
   }

   Date operator - (int daysToSub) // binary subtraction
   {
      return Date(month, day - daysToSub, year);
   }

   void DisplayDate()
   {
      cout << month << " / " << day << " / " << year << endl;
   }
};

int main()
{
   Date holiday (7, 24, 2024);
   cout << "Holiday on: ";
   holiday.DisplayDate ();

   Date previousHoliday (holiday - 19);
   cout << "Previous holiday on: ";
   previousHoliday.DisplayDate();

   Date nextHoliday(holiday + 6);
   cout << "Next holiday on: ";
   nextHoliday.DisplayDate ();

   return 0;
}
```

Output

```
Holiday on: 7 / 24 / 2024 
Previous holiday on: 12 / 5 / 2024 
Next holiday on: 12 / 30 / 2024
```
