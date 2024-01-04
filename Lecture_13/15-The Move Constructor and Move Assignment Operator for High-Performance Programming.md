[//]: # (### The Move Constructor and Move Assignment Operator for High-Performance Programming)

The move constructor and move assignment operator are essential features introduced in C++11 to optimize performance, especially for managing resources in high-performance scenarios. They facilitate the efficient transfer of resources (like memory, ownership of dynamically allocated data) from one object to another, reducing unnecessary copying and enhancing performance.

#### The Problem of Unwanted Copy Steps

If the `MyBuffer` class, as demonstrated in a last example supported the addition operator, the following lines of code would be valid examples of easy concatenation:

```cpp
MyBuffer buf1(5); 
MyBuffer buf2(15); 
MyBuffer buf3(buf1+buf2); // operator+, copy constructor 
MyBuffer bufSum (1); 
bufSum = buf1 + buf2 + buf3; // operator+, copy constructor, copy assignment
```

Thus, the useful operators that help with concatenation and assignment cause performance problems because multiple internal copy steps are required. The copy constructor, for instance, executes a deep copy to a temporary value that does not exist after the expression.

This problem has been resolved through the introduction of move constructors and move assignment operators.

#### Declaring a Move Constructor and Move Assignment Operator

```cpp
class Sample 
{ 
private: 
    Type* ptrResource; 
public: 
    Sample(Sample&& moveSource) // Move constructor, note && 
    { 
        ptrResource = moveSource.ptrResource; // take ownership, start move 
        moveSource.ptrResource = NULL; 
    } 
    Sample& operator= (Sample&& moveSource) //move assignment operator, note & 
    { 
        if(this != &moveSource) 
        { 
            delete [] ptrResource; // free own resource
            ptrResource = moveSource.ptrResource; // take ownership, start move 
            moveSource.ptrResource = NULL; // free move source of ownership 
        } 
    } 
    Sample(); // default constructor 
    Sample(const Sample& copySource); // copy constructor 
    Sample& operator= (const Sample& copySource); // copy assignment
}
```

Standard-compliant compilers ensure that for rvalue temporaries, the move constructor is used instead of the copy constructor, and the move assignment operator is invoked instead of the copy assignment operator.

In your implementation of these two, you ensure that instead of copying, you are simply moving the resource from the source to the destination.

The following program demonstrates the effectiveness of these two recent additions in optimizing the class `MyBuffer`.

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
      cout << "Constructing new instance with " \
           << length << " elements" << endl;
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

   MyBuffer(MyBuffer&& src) // move constructor
   {
      cout << "Move constructor transferring ownership" << endl;

      if (src.myNums != NULL)
      {
         bufLength = src.bufLength;
         myNums = src.myNums; // take ownership

         src.myNums = NULL;
         src.bufLength = 0;
      }
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

   MyBuffer& operator= (MyBuffer&& src) // move assignment
   {
      cout << "Move assignment transferring ownership" << endl;

      if ((src.myNums != NULL) && (myNums != src.myNums))
      {
         delete[] myNums;
         myNums = src.myNums; // take ownership
         bufLength = src.bufLength;

         src.bufLength = 0;
         src.myNums = NULL;
      }

      return *this;
   }

   MyBuffer operator + (const MyBuffer& bufToAppend)
   {
      cout << "Operator + concatenating" << endl;
      MyBuffer newBuf(this->bufLength + bufToAppend.bufLength);

      for (unsigned int counter = 0; counter < bufLength; ++counter)
         newBuf.SetValue(counter, *(myNums + counter));

      for (unsigned int counter = 0; counter < bufToAppend.bufLength; ++counter)
         newBuf.SetValue(counter + bufLength, *(bufToAppend.myNums + counter));

      return newBuf;
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
   MyBuffer buf1(5);
   MyBuffer buf2(15);

   cout << "Concatenation at object instantiation: " << endl;
   MyBuffer buf3(buf1 + buf2); 
   MyBuffer bufSum(1);

   cout << "Concatenation at assignment: " << endl;
   bufSum = buf1 + buf2 + buf3;  

   return 0;
}
```

Output
Output without the move constructor and move assignment operator:

```
Constructing new instance with 5 elements
Constructing new instance with 15 elements
Concatenation at object instantiation: 
Operator + concatenating
Constructing new instance with 20 elements
Copy constructor creating deep copy
Constructing new instance with 1 elements
Concatenation at assignment: 
Operator + concatenating
Constructing new instance with 20 elements
Copy constructor creating deep copy
Operator + concatenating
Constructing new instance with 40 elements
Copy constructor creating deep copy
Copy Assignment creating deep copy
```

Output with the move constructor and move assignment operator enabled

```
Constructing new instance with 5 elements
Constructing new instance with 15 elements
Concatenation at object instantiation: 
Operator + concatenating
Constructing new instance with 20 elements
Move constructor transferring ownership
Constructing new instance with 1 elements
Concatenation at assignment: 
Operator + concatenating
Constructing new instance with 20 elements
Move constructor transferring ownership
Operator + concatenating
Constructing new instance with 40 elements
Move constructor transferring ownership
Move assignment transferring ownership
```

Note that the move constructor and the move assignment operator are optional; they are not essential to the correct functioning of a program. However, they enable an immense improvement in performance and reduction in resource consumption. Unlike with the copy constructor and the copy assignment operator, the compiler does not add a default implementation of the move constructor or the move assignment operator for you.
