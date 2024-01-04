[//]: # (### The Subscript Operator [])

The operator that allow, array-style ([]) access to a class is called a *subscript operator*.

The typical syntax of a subscript operator is

```cpp
return_type& operator [] (subscript_type& subscript);
```

So, when creating a class such as `MyBuffer` that encapsulates a dynamic array class of characters in a `char* buffer`, a subscript operator makes it really easy to randomly access individual characters in the buffer:

```cpp
class MyBuffer 
{ 
    // ... other class members 
public: 
    /*const*/ char& operator [] (int index) /*const*/ 
    { 
        // return the char at position index in buffer 
    } 
};
```

The following program demonstrates how the subscript operator (`[]`) helps a user iterate through the characters contained in an instance of MyBuffer using normal array semantics.

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

   int& operator[] (unsigned int index)
   {
      return myNums[index];
   }

   // const version will be used by const instances of MyBuffer
   const int& operator[] (unsigned int index) const
   {
      return myNums[index];
   }

   MyBuffer(const MyBuffer& src) 
   {
      cout << "Copy constructor creating deep copy" << endl;
      bufLength = src.bufLength;
      myNums = new int[bufLength];
      copy(src.myNums, src.myNums + bufLength, myNums); // deep copy
   }

   MyBuffer& operator= (const MyBuffer& src) 
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
      cin >> buf[counter];
   }

   for (unsigned int counter = 0; counter < numsToStore; ++counter)
      cout << "Value " << counter << " is " << buf[counter] << endl;

   // const MyBuffer bufConst(1); // requires const variant of operator[]
   return 0;
}
```

Output

```
How many integers would you like to store? 3 
Enter value: 101 
Enter value: 202 
Enter value: -101 
Value 0 is 101 
Value 1 is 202 
Value 2 is -101
```

**Caution**
>Using the keyword `const` is important even when programming operators. To ensure that the subscript operator (`[]`) can be used only to read data and not to change data, you would do well to define the operator as

```cpp
const int& operator[] (unsigned int index) const
{ 
    return myNums[index]; 
}
```

>By using `const`, you protect the internal member `MyBuffer::myNums` against direct modification from the outside via operator`[]`. In addition to classifying the return value as `const`, you restrict the operator function type to `const` to ensure that it cannot modify the class’s member attributes.
