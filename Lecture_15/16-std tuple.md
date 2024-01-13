[//]: # (### std::tuple)

The support of variadic templates has also helped in standard support for tuples.

`std::tuple` is a template class in C++ introduced in the C++11 standard. It is part of the Standard Template Library (STL) and provides a convenient way to group together multiple values into a single object.

A `std::tuple` can store heterogeneous types, meaning each element can have a different type. These elements may be individually accessed using the standard library function `std::get`.

The following code  demonstrates the instantiation and use of a `std::tuple`.

```cpp
#include <iostream>
#include <tuple>
#include <string>
using namespace std;

template <typename tupleType>
void DisplayTupleInfo(tupleType& tup)
{
   const int numMembers = tuple_size<tupleType>::value;
   cout << "Num elements in tuple: " << numMembers << endl;
   cout << "Last element value: " << get<numMembers - 1>(tup) << endl;
}

int main()
{
   tuple<int, char, string> tup1(make_tuple(101, 's', "Hello Tuple!"));
   DisplayTupleInfo(tup1);

   auto tup2(make_tuple(3.14, false));
   DisplayTupleInfo(tup2);

   auto concatTup(tuple_cat(tup2, tup1)); // contains tup2, tup1 members
   DisplayTupleInfo(concatTup);

   double pi;
   string sentence;
   tie(pi, ignore, ignore, ignore, sentence) = concatTup;
   cout << "Unpacked! Pi: " << pi << " and \"" << sentence << "\"" << endl;

    return 0;
}
```

Output

```
Num elements in tuple: 3 
Last element value: Hello Tuple! 
Num elements in tuple: 2 
Last element value: 0 
Num elements in tuple: 5 
Last element value: Hello Tuple! 
Unpacked! Pi: 3.14 and “Hello Tuple!”
```

This example uses the `std::tuple` class to instantiate different tuples containing varying number and types of elements.

The code contains three different instantiations of a `std::tuple`. `tup1` contains three members: an `int`, a `char`, and a `std::string`. `tup2` contains a `double` and a `bool` and also uses the compiler’s automatic type deduction feature via the keyword `auto`. `tup3` is actually a tuple with five members: `double`, `bool`, `int`, `char`, and `string`—a result of concatenation using the template function `std::tuple_cat`.

The template function `DisplayTupleInfo()`  demonstrates a use of `tuple_size` that resolves to the number of elements contained by that specific instantiation of `std::tuple` during compilation.

`std::get` is the mechanism to access individual values stored in a tuple using their zero-based indexes.

Finally, `std::tie`  demonstrates how the contents of a tuple can be unpacked or copied into individual objects. You use `std::ignore` to instruct tie to ignore the tuple members that were not of any interest to the application.
