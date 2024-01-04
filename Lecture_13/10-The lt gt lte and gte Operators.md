[//]: # (### The <, >, <=, and >= Operators)

We need to program the `<`, `>`, `<=`, and `>=` operators to enable conditional checking like the following:

```cpp
if (date1 < date2) {// do something}
```

These operators are demonstrated in the following code:

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
   
   bool operator< (const Date& compareTo)
   {
      if (year < compareTo.year)
         return true;
      else if ((year == compareTo.year) && (month < compareTo.month))
         return true;
      else if ((year == compareTo.year) && (month == compareTo.month) 
               && (day < compareTo.day))
         return true;
      else
         return false;
   }

   bool operator<= (const Date& compareTo)
   {
      if (this->operator== (compareTo))
         return true;
      else
         return this->operator< (compareTo);
   }

   bool operator > (const Date& compareTo)
   {
      return !(this->operator<= (compareTo));
   }

   bool operator== (const Date& compareTo)
   {
      return ((day == compareTo.day)
         && (month == compareTo.month)
         && (year == compareTo.year));
   }
   
   bool operator>= (const Date& compareTo)
   {
      if(this->operator== (compareTo))
         return true;
      else
         return this->operator> (compareTo);
   }

   void DisplayDate()
   {
      cout << month << " / " << day << " / " << year << endl;
   }
};
   
int main()
{
   Date holiday1 (7, 25, 2024);
   Date holiday2 (7, 31, 2024);

   cout << "holiday 1 is: ";
   holiday1.DisplayDate();
   cout << "holiday 2 is: ";
   holiday2.DisplayDate();

   if (holiday1 < holiday2)
      cout << "operator<: holiday1 happens first" << endl;

   if (holiday2 > holiday1)
      cout << "operator>: holiday2 happens later" << endl;

   if (holiday1 <= holiday2)
      cout << "operator<=: holiday1 happens on or before holiday2" << endl;
   
   if (holiday2 >= holiday1)
      cout << "operator>=: holiday2 happens on or after holiday1" << endl;

   return 0;
}
```

Output

```
holiday 1 is: 7 / 25 / 2024
holiday 2 is: 7 / 31 / 2024
operator<: holiday1 happens first
operator>: holiday2 happens later
operator<=: holiday1 happens on or before holiday2
operator>=: holiday2 happens on or after holiday1
```
