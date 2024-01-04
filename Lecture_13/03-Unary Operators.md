[//]: # (### Unary Operators)

A unary operator is an operator that functions on a single operand. A unary operator that is implemented in the global namespace or as a static member function of a class uses the following structure:

```cpp
return_type operator operator_type (parameter_type) 
{ 
    // ... implementation 
}
```

A unary operator that is a (non-static) member of a class has a similar structure but is lacking in parameters because the single parameter that it works on is the instance of the class itself (`*this`):

```cpp
return_type operator operator_type() 
{ 
    // ... implementation 
}
```

Here's a table listing the unary operators that can be overloaded in C++:

| Operator   | Description                      |
|------------|----------------------------------|
| +          | Unary plus                       |
| -          | Unary minus                      |
| ++         | Prefix and postfix increment     |
| --         | Prefix and postfix decrement     |
| *          | Pointer dereference              |
| &          | Address of                       |
| !          | Logical NOT                      |
| ~          | Bitwise NOT                      |
| ->         | Member selection                 |
| new        | Memory allocation                |
| delete     | Memory deallocation              |

> `sizeof()` is a unary operator that cannot be overloaded

#### Unary Increment (`++`) and Decrement (`--`) Operators

A unary prefix increment operator (`++`) can be programmed using the following syntax within the class declaration:

```cpp
class MyClass {
public:
    

    // Overloading the prefix increment operator
    MyClass& operator++() {
        // Define the behavior for prefix increment
        
        return *this;
    }
};
```

The postfix increment operator (`++`), on the other hand, has a different return type and an input parameter (which is not used):

```cpp
class MyClass {
public:
   
    // Overloading the postfix increment operator
    MyClass operator++(int) {
        // Store the current state of the object
        MyClass temp = *this;

        // Define the behavior for postfix increment
        
        // Return the stored original state
        return temp;
    }
};
```

The prefix and postfix decrement operators have syntax similar to that of the increment operators; however, the declaration of a decrement operator contains a `--` instead of a `++`.

The following example shows a simple class `Date` that allows you to increment days by using the `++` operator.

```cpp
// also contains postfix increment and decrement

#include <iostream>
using namespace std;

class Date
{
private:
   int day, month, year;

public:
   Date (int inMonth, int inDay, int inYear)
        : month (inMonth), day(inDay), year (inYear) {};

   Date& operator ++ () // prefix increment
   {
      ++day;
      return *this;
   }

   Date& operator -- () // prefix decrement
   {
      --day;
      return *this;
   }

   Date operator ++ (int) // postfix increment
   {
      Date copy(month, day, year);
      ++day;
      return copy;
   }

   Date operator -- (int) // postfix decrement
   {
      Date copy(month, day, year);
      --day;
      return copy;
   }

   void DisplayDate()
   {
      cout << month << " / " << day << " / " << year << endl;
   }
};

int main ()
{
   Date independenceDay (7, 5, 1962); // Jul 5, 1962

   cout << "The date object is initialized to: ";
   independenceDay.DisplayDate ();

   ++independenceDay; // move date ahead by a day
   cout << "Date after prefix-increment is: ";
   independenceDay.DisplayDate ();

   --independenceDay; // move date backwards by a day
   cout << "Date after a prefix-decrement is: ";
   independenceDay.DisplayDate ();

   return 0;
}
```

Output

```
The date object is initialized to: 7 / 5 / 1962 
Date after prefix-increment is: 7 / 6 / 1962 
Date after a prefix-decrement is: 7 / 5 / 1962
```

>**Note**
>This version of a date class has a bare minimum implementation to reduce the number of code lines and to explain how the prefix operators `++` and `--` are to be implemented. A professional version of this example would implement rollover functionalities for month and year and take into consideration leap years as well.

To support postfix increment or decrement, you simply add the following code to the `Date` class:

```cpp
// postfix differs from prefix operator in return-type and parameters 
Date operator ++ (int) // postfix increment 
{ 
    Date copy(month, day, year); 
    ++day; 
    return copy; // copy of instance before increment returned 
} 
Date operator -- (int) // postfix decrement 
{ 
    Date copy(month, day, year); 
    --day; 
    return copy; // copy of instance before decrement returned 
}
```

When your version of the `Date` class supports both prefix and postfix increment and decrement operators, you can use objects of the `Date` class as follows:

```cpp
Date holiday (7, 4, 2024); // instantiate 
++ holiday; // using prefix increment operator++ 
holiday ++; // using postfix increment operator++ 
-- holiday; // using prefix decrement operator 
-- holiday --; // using postfix decrement operator --
```

>**Note**
>As the implementation of the postfix operators demonstrates, a copy containing the initial state of the object is created before the increment or decrement operation. This copy is returned to the caller. In other words, if you have a choice between using ++object; and object++; to essentially only increment, you should choose the former to avoid creating a temporary copy that will not be used.
