[//]: # (### The Addition Assignment += and Subtraction Assignment -= Operators)

The addition assignment operator allows syntax such as `a += b;`, which allows you to increment the value of an object `a` by an amount `b`. Then, the addition assignment operator can be overloaded to accept different types of parameter `b`. The following code allows you to add an integer value to a `Date` object.

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

   void operator+= (int daysToAdd) // addition assignment
   {
      day += daysToAdd;
   }

   void operator-= (int daysToSub) // subtraction assignment
   {
      day -= daysToSub;
   }

   void DisplayDate()
   {
      cout << month << " / " << day << " / " << year << endl;
   }
};
   
int main()
{
   Date holiday (7, 24, 2024);
   cout << "holiday is on: ";
   holiday.DisplayDate ();

   cout << "holiday -= 19 gives: ";
   holiday -= 19;
   holiday.DisplayDate();

   cout << "holiday += 25 gives: ";
   holiday += 25;
   holiday.DisplayDate ();

   return 0;
}
```

Output

```
holiday is on: 7 / 25 / 2024 
holiday -= 19 gives: 7 / 5 / 2024 
holiday += 25 gives: 7 / 30 / 2024
```

**Note**

> `*=`,  `/=`,  `%=`,  `-=`,  `<<=`,  `>>=`,  `^=`,  `|=`, and  `&=` operators have syntax similar to that of the addition assignment operator shown in this example.

> Although the ultimate objective of overloading operators is making a class easy and intuitive to use, there are many situations where implementing an operator might not make sense. For example, the calendar class `Date` has absolutely no use for a bitwise AND assignment operator (`&=`). No user of this class should ever expect (or even think of) getting useful results from an operation such as `greatDay &= 20`;.
