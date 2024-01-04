[//]: # (### The Copy Assignment Operator =)

There are times when we want to assign the contents of an instance of one class to another class, like this:

```cpp
Date holiday(7, 5, 2024); 
Date anotherHoliday(11, 1, 2023); 
anotherHoliday = holiday; // uses copy assignment operator 

```

This assignment invokes the default copy assignment operator that the compiler has built into a class when you have not supplied one.

Depending on the nature of the class, the default copy assignment operator might be inadequate, especially if the class is managing a resource that will not be copied.

This problem with the default copy assignment operator is similar to the problem with the default copy constructor discussed in Lesson 10.

To ensure deep copies, as with the copy constructor, you need to specify an accompanying copy assignment operator:

```cpp
ClassType& operator= (const ClassType& copySource) 
{ 
    if(this != &copySource) // protection against copy into self 
    { 
        // copy assignment operator implementation 
    } 
    return *this; 
}

```

Deep copies are important if a class encapsulates a raw pointer. To ensure deep copies during assignments, you define a copy assignment operator as shown in the following code.

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

class MyBuffer
{
private:
   int* myNums;
   unsigned int bufLength;

public:
   MyBuffer(unsigned int length)
   {
      bufLength = length;
      myNums = new int[length]; // allocate memory
   }

   MyBuffer(const MyBuffer& src) // copy constructor
   {
      cout << "Copy constructor creating deep copy" << endl;
      bufLength = src.bufLength;
      myNums = new int[bufLength];
      copy(src.myNums, src.myNums + bufLength, myNums); // deep copy
   }

   MyBuffer& operator= (const MyBuffer& src) // copy assignment
   {
      cout << "Copy Assignment creating deep copy" << endl;
      if (myNums != src.myNums) // avoid copy to self
      {
         if (myNums)
            delete myNums;

         bufLength = src.bufLength;
         myNums = new int[bufLength];
         copy(src.myNums, src.myNums + bufLength, myNums); // deep copy
      }

      return *this;
   }

   ~MyBuffer()
   {
      delete[] myNums; // free allocated memory
   }

   void SetValue(unsigned int index, int value)
   {
      if (index < bufLength) // check for bounds
         *(myNums + index) = value;
   }

   void DisplayBuf()
   {
      for (unsigned int counter = 0; counter < bufLength; ++counter)
         cout << *(myNums + counter) << " ";

      cout << endl;
   }
};

int main()
{
   cout << "How many integers would you like to store? ";
   unsigned int numsToStore = 0;
   cin >> numsToStore;

   MyBuffer buf(numsToStore);
   for (unsigned int counter = 0; counter < numsToStore; ++counter)
   {
      cout << "Enter value: ";
      int valueEntered = 0;
      cin >> valueEntered;
      buf.SetValue(counter, valueEntered);
   }

   MyBuffer anotherBuf(1); // initialize to contain just 1 int
   anotherBuf = buf;
   anotherBuf.DisplayBuf();

   return 0; 
}
```

Output

```
How many integers would you like to store? 3 
Enter value: 101 
Enter value: 202 
Enter value: 303 
Copy Assignment creating deep copy 
101 202 303
```

**Tip**
>`std::copy()` is one among many useful algorithms supplied by the Standard Template Library. You need to include the header `<algorithm>` to use it.

**Tip**
>To create a class that cannot be copied, declare the copy constructor and copy assignment operator as private. Declaration as private without implementation is sufficient for the compiler to throw errors on all attempts at copying this class by passing to a function by value or assigning one instance into another.
