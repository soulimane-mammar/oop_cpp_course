[//]: # (### Template Functions)

Imagine a function that would adapt itself to suit parameters of different types, without requiring you to define an overloaded version for each type. Such a function is possible using template syntax

Let’s analyze a sample template declaration that is the equivalent of the previously discussed macro `MAX`, which returns the greater of two supplied parameters:

```cpp
template <typename T> 
const T& getMax(const T& v1, const T& v2) 
{ 
    if (v1 > v2) 
        return v1;
    else 
        return v2; 
}
```

Sample usage

```cpp
int num1 = 25; 
int num2 = 40; 
int maxVal = getMax<int>(num1, num2); 
double double1 = 1.1; 
double double2 = 1.001; 
double maxVal = GetMax<double>(double1, double2);
```

Note the detail `<int>` that is used in the call to `getMax`. It effectively defines the template parameter `T` as `int`. Based on the preceding code, the compiler generates two versions of the template function `getMax`, which can be visualized as follows:

```cpp
const int& getMax(const int& v1, const int& v2) 
{ 
    //... 
} 

const double& getMax(const double& v1, const double& v2) 
{ 
    // ... 
}
```

In reality, however, template functions don’t necessarily need an accompanying type specifier. So, the following function call works perfectly well:

```cpp
int maxVal =getMax(num1, num2); 
```

Compilers are intelligent enough to understand that the template function is being invoked for the integer type. With template classes, however, you need to explicitly specify type, as shown in the following code.

```cpp
#include<iostream>
#include<string>
using namespace std;

template <typename T>
const Type& getMax (const T& v1, const T& v2)
{
    if (v1 > v2)
        return v1;
    else
        return v2;
}

template <typename T>
void DisplayComparison(const T& v1, const T& v2)
{
   cout << "getMax(" << v1 << ", " << v2 << ") = ";
   cout << getMax(v1, v2) << endl;
}

int main()
{
   int num1 = -101, num2 = 2011;
   DisplayComparison<int>(num1, num2);

   double d1 = 3.14, d2 = 3.1416;
   DisplayComparison(d1, d2);

   string name1("Mehdi"), name2("Mounir");
   DisplayComparison(name1, name2);

   return 0;
}
```

Output

```
getMax(-101, 2011) = 2011 
getMax(3.14, 3.1416) = 3.1416 
getMax(Mehdi, Mounir) = Mounir
```

### Templates and Type Safety

The template functions `DisplayComparison()` and `getMax()`in the previous program are type safe. This means that they would not allow a meaningless call like this one:

```cpp
DisplayComparison(num1, name1); 
```

Such a call would immediately result in a compile failure.
