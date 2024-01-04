[//]: # (### Binary Operators)

An operator that functions on two operands is called a binary operator. You define a binary operator implemented as a global function or a static member function by using the following syntax:

```cpp
return_type operator_type (parameter1, parameter2);
```

 You define a binary operator implemented as a class member by using the following syntax:

 ```cpp
 return_type operator_type (parameter);
 ```

The reason the class member version of a binary operator accepts only one parameter is that the second parameter is usually derived from the attributes of the class itself.

#### Overloadable Binary Operators

Absolutely! Here's an expanded table that includes both the binary operators and additional operators like assignment operators and the subscript operator:

| Operator | Description                                     | Member Function Signature                                | Non-Member (Free) Function Signature                                   |
|----------|-------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------------------------|
| +        | Addition                                        | `ReturnType operator+(const OperandType&) const;`         | `ReturnType operator+(const OperandType&, const OperandType&);`         |
| -        | Subtraction                                     | `ReturnType operator-(const OperandType&) const;`         | `ReturnType operator-(const OperandType&, const OperandType&);`         |
| *        | Multiplication                                  | `ReturnType operator*(const OperandType&) const;`         | `ReturnType operator*(const OperandType&, const OperandType&);`         |
| /        | Division                                        | `ReturnType operator/(const OperandType&) const;`         | `ReturnType operator/(const OperandType&, const OperandType&);`         |
| %        | Modulo (Remainder after division)               | `ReturnType operator%(const OperandType&) const;`         | `ReturnType operator%(const OperandType&, const OperandType&);`         |
| ==       | Equality comparison                             | `bool operator==(const OperandType&) const;`              | `bool operator==(const OperandType&, const OperandType&)`                 |
| !=       | Inequality comparison                           | `bool operator!=(const OperandType&) const;`              | `bool operator!=(const OperandType&, const OperandType&)`                 |
| <        | Less than comparison                            | `bool operator<(const OperandType&) const;`               | `bool operator<(const OperandType&, const OperandType&)`                  |
| <=       | Less than or equal to comparison                | `bool operator<=(const OperandType&) const;`              | `bool operator<=(const OperandType&, const OperandType&)`                 |
| >        | Greater than comparison                         | `bool operator>(const OperandType&) const;`               | `bool operator>(const OperandType&, const OperandType&)`                  |
| >=       | Greater than or equal to comparison             | `bool operator>=(const OperandType&) const;`              | `bool operator>=(const OperandType&, const OperandType&)`                 |
| &&       | Logical AND                                     | `bool operator&&(const OperandType&) const;`              | `bool operator&&(const OperandType&, const OperandType&)`                 |
| \|\|     | Logical OR                                      | `bool operator\|\|(const OperandType&) const;`            | `bool operator\|\|(const OperandType&, const OperandType&)`               |
| &        | Bitwise AND                                     | `ReturnType operator&(const OperandType&) const;`         | `ReturnType operator&(const OperandType&, const OperandType&);`         |
| \|       | Bitwise OR                                      | `ReturnType operator\|(const OperandType&) const;`        | `ReturnType operator\|(const OperandType&, const OperandType&);`        |
| ^        | Bitwise XOR                                     | `ReturnType operator^(const OperandType&) const;`         | `ReturnType operator^(const OperandType&, const OperandType&);`         |
| <<       | Bitwise left shift                              | `ReturnType operator<<(const OperandType&) const;`        | `ReturnType operator<<(const OperandType&, const OperandType&);`        |
| >>       | Bitwise right shift                             | `ReturnType operator>>(const OperandType&) const;`        | `ReturnType operator>>(const OperandType&, const OperandType&);`        |
| =        | Assignment                                      | `ReturnType& operator=(const OperandType&);`              | N/A                                                                     |
| +=       | Addition assignment                             | `ReturnType& operator+=(const OperandType&);`             | N/A                                                                     |
| -=       | Subtraction assignment                          | `ReturnType& operator-=(const OperandType&);`             | N/A                                                                     |
| *=       | Multiplication assignment                       | `ReturnType& operator*=(const OperandType&);`             | N/A                                                                     |
| /=       | Division assignment                             | `ReturnType& operator/=(const OperandType&);`             | N/A                                                                     |
| %=       | Modulo assignment                               | `ReturnType& operator%=(const OperandType&);`             | N/A                                                                     |
| &=       | Bitwise AND assignment                          | `ReturnType& operator&=(const OperandType&);`             | N/A                                                                     |
| \|=      | Bitwise OR assignment                           | `ReturnType& operator\|=(const OperandType&);`            | N/A                                                                     |
| ^=       | Bitwise XOR assignment                          | `ReturnType& operator^=(const OperandType&);`             | N/A                                                                     |
| <<=      | Bitwise left shift assignment                   | `ReturnType& operator<<=(const OperandType&);`            | N/A                                                                     |
| >>=      | Bitwise right shift assignment                  | `ReturnType& operator>>=(const OperandType&);`            | N/A                                                                     |
| []       | Subscript (Array access)                        | `ReturnType operator[](const OperandType&);`              | `ReturnType operator[](const OperandType&, const OperandType&);`       |

Please note:

- The subscript operator `[]` is used to access elements of an array or a container-like object.
- For the subscript operator, the non-member function signature includes the object
