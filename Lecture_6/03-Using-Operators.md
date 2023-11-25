[//]: # (### Using Operators)

In C++, operators are symbols used to perform operations on variables, constants, and expressions. These operations can include arithmetic, logical, bitwise, assignment, comparison, and more. Here's an overview of different types of operators in C++:

#### 1. **Arithmetic Operators:**

- Perform mathematical operations like addition, subtraction, multiplication, division, and modulus.

   ```cpp
   int a = 10 + 5;  // Addition
   int b = 20 - 7;  // Subtraction
   int c = 6 * 4;   // Multiplication
   int d = 25 / 5;  // Division
   int e = 15 % 4;  // Modulus (remainder)
   ```

#### 2. **Assignment Operators:**

In C++, the assignment operator (`=`) is used to assign a value to a variable. However, understanding the concepts of lvalues and rvalues is essential in the context of assignments.

##### Lvalues and Rvalues

- **Lvalue:** An lvalue refers to an object that has a memory location and can be assigned a value. Lvalues are generally things that can appear on the left side of an assignment. Variables, references, and dereferenced pointers are examples of lvalues.

  Example:

  ```cpp
  int x = 10;  // x is an lvalue as it can appear on the left side of an assignment
  ```

- **Rvalue:** An rvalue refers to a value that is addressless and typically appears on the right side of an assignment. Rvalues are temporary and do not have a persistent memory location. Literals, temporary values, and results of expressions are examples of rvalues.

  Example:

  ```cpp
  int y = 5 + 3;  // The result of the expression (5 + 3) is an rvalue
  ```

##### Assignment Operator and Lvalues/Rvalues

- The assignment operator (`=`) in C++ takes an lvalue on its left-hand side and an rvalue on its right-hand side.

  Example:

  ```cpp
  int x = 10;  // x is an lvalue, and 10 is an rvalue
  x = 20;      // Assignment operator: x (lvalue) gets the value of 20 (rvalue)
  ```

- Assigning an rvalue to an lvalue is valid, as long as the type matches or is convertible.

  Example:

  ```cpp
  int x;
  x = 30;  // Valid: Assigning an rvalue (30) to an lvalue (x)
  ```

#### 3. **Comparison Operators:**

In C++, there are several comparison operators used to compare values and return a Boolean result (`true` or `false`). Here are all the comparison operators in C++:

##### 1. **Equal to (`==`):**

- Checks if two values are equal.

   ```cpp
   int x = 5, y = 7;
   bool isEqual = (x == y);  // Returns false
   ```

##### 2. **Not equal to (`!=`):**

- Checks if two values are not equal.

   ```cpp
   int a = 10, b = 20;
   bool notEqual = (a != b);  // Returns true
   ```

##### 3. **Greater than (`>`):**

- Checks if the left operand is greater than the right operand.

   ```cpp
   int m = 15, n = 9;
   bool isGreater = (m > n);  // Returns true
   ```

##### 4. **Less than (`<`):**

- Checks if the left operand is less than the right operand.

   ```cpp
   int p = 5, q = 10;
   bool isLess = (p < q);  // Returns true
   ```

##### 5. **Greater than or equal to (`>=`):**

- Checks if the left operand is greater than or equal to the right operand.

   ```cpp
   int r = 25, s = 25;
   bool greaterOrEqual = (r >= s);  // Returns true
   ```

##### 6. **Less than or equal to (`<=`):**

- Checks if the left operand is less than or equal to the right operand.

   ```cpp
   int t = 30, u = 40;
   bool lessOrEqual = (t <= u);  // Returns true
   ```

These comparison operators return a Boolean result (`true` or `false`) based on the evaluation of the comparison between two values or expressions. They are commonly used in conditional statements, loops, and other scenarios where comparisons are required in C++ programs.

#### 4. **Logical Operators:**

- Perform logical operations (`&&`, `||`, `!`) on Boolean values.

   ```cpp
   bool p = true, q = false;
   bool andResult = (p && q);  // Logical AND
   bool orResult = (p || q);   // Logical OR
   bool notResult = !p;        // Logical NOT
   ```

#### 5. **Bitwise Operators:**

- Perform operations at the bit level (`&`, `|`, `^`, `~`, `<<`, `>>`).

   ```cpp
   int m = 5, n = 3;
   int bitAnd = (m & n);     // Bitwise AND
   int bitOr = (m | n);      // Bitwise OR
   int bitXor = (m ^ n);     // Bitwise XOR
   int bitNot = (~m);        // Bitwise NOT
   int leftShift = (m << 2); // Left shift
   int rightShift = (m >> 1);// Right shift
   ```

#### 6. **Increment and Decrement Operators:**

In C++, the increment (`++`) and decrement (`--`) operators are used to increase or decrease the value of a variable by one, respectively. These operators can be applied in different ways, distinguishing between pre-increment, post-increment, pre-decrement, and post-decrement.

###### **Post-increment (`variable++`):**

- The value is first used in an expression, and then it is incremented by one.

   ```cpp
   int x = 5;
   int y = x++;  // y gets the value of x (5), then x is incremented
   // Now, x = 6, y = 5
   ```

###### **Pre-increment (`++variable`):**

- The value is incremented by one first, and then the updated value is used in the expression.

   ```cpp
   int a = 10;
   int b = ++a;  // a is incremented first, then b gets the updated value of a
   // Now, a = 11, b = 11
   ```

##### **Post-decrement (`variable--`):**

- The value is first used in an expression, and then it is decremented by one.

   ```cpp
   int m = 8;
   int n = m--;  // n gets the value of m (8), then m is decremented
   // Now, m = 7, n = 8
   ```

##### **Pre-decrement (`--variable`):**

- The value is decremented by one first, and then the updated value is used in the expression.

   ```cpp
   int p = 15;
   int q = --p;  // p is decremented first, then q gets the updated value of p
   // Now, p = 14, q = 14
   ```

##### Additional Notes

- **Usage:** Increment and decrement operators can be used on integral and floating-point types.
- **Side Effects:** Avoid complex expressions using increment/decrement within the same statement as it can lead to confusion and unexpected behavior.
- **Overuse:** Overusing these operators in complex code can make the code less readable, so use them judiciously.

#### 7. **Conditional Operator (Ternary Operator):**

The ternary operator, also known as the conditional operator (`? :`), is a unique operator in C++ that evaluates a condition and returns one of two expressions based on the result of the condition. It serves as a compact way to express simple conditional statements.

##### Syntax

```cpp
(condition) ? expressionIfTrue : expressionIfFalse;
```

##### Explanation

- **`condition`:** A Boolean expression that determines which of the two expressions will be evaluated.
- **`expressionIfTrue`:** The value returned if the condition evaluates to `true`.
- **`expressionIfFalse`:** The value returned if the condition evaluates to `false`.

##### Example

```cpp
int x = 10, y = 20;
int maxVal = (x > y) ? x : y; // Assigns the larger value of x and y to maxVal
```

In this example:

- If `x > y` is `true`, `x` is assigned to `maxVal`.
- If `x > y` is `false`, `y` is assigned to `maxVal`.

##### Usage

- The ternary operator is often used in assignments, especially when choosing between two values based on a condition.
- It is also commonly used in expressions where simple conditional logic is required without the overhead of an `if-else` statement.

##### Considerations

- It's essential to keep the expressions simple to maintain readability.
- Overuse of the ternary operator in complex statements can make the code less understandable.

The ternary operator provides a concise way to express simple conditional logic in C++, particularly when assigning values based on a condition. However, its readability diminishes if used excessively or with overly complex expressions.

#### C++20 Three-Way Comparison Operator (<=>)

The three-way comparison operator (`<=>`), introduced in C++20, is a spaceship operator that performs a combined comparison of two values and returns a value indicating their relationship. It provides a way to directly compare two values and obtain the relationship between them, simplifying comparison operations and supporting various scenarios like sorting, searching, and ordering objects.

##### Syntax

```cpp
result = expression1 <=> expression2;
```

##### Return Values

The `<=>` operator returns one of three values:

- Negative value (`-1`): Indicates `expression1` is less than `expression2`.
- Zero (`0`): Indicates `expression1` is equal to `expression2`.
- Positive value (`1`): Indicates `expression1` is greater than `expression2`.

##### Example

```cpp
auto result = 5 <=> 8;  // result = -1 (5 is less than 8)
auto res = "Hello" <=> "World";  // result = -1 (lexicographical comparison)
```

##### Note

- The `<=>` operator requires compiler support for C++20 or later standards.

#### `sizeof()` Operator to Determine the Memory Occupied by a Variable

The `sizeof` operator is used to determine the size, in bytes, of a type or a variable. It is a compile-time (except for VLAs) operator that returns the number of bytes occupied by a variable or a data type.

##### 1. **Size of a Type:**

- Using `sizeof` with a type name provides the size of that type.

   ```cpp
   sizeof(int);     // Returns the size of an integer in bytes
   sizeof(double);  // Returns the size of a double in bytes
   ```

##### 2. **Size of a Variable:**

- `sizeof` can also be used with a variable to get its size in bytes.

   ```cpp
   int arr[10];
   sizeof(arr);  // Returns the size of the entire array in bytes
   ```

##### Behavior

- The `sizeof` operator determines the size based on the architecture and compiler. It's commonly measured in bytes.
- The size obtained by `sizeof` includes any padding that might be added by the compiler to align the data in memory.
- It's particularly useful when working with arrays, structures, or determining the appropriate allocation of memory.

##### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Size of int: " << sizeof(int) << " bytes" << endl;
    
    double value;
    cout << "Size of double variable: " << sizeof(value) << " bytes" << endl;

    int arr[10];
    cout << "Size of array: " << sizeof(arr) << " bytes" << endl;

    return 0;
}
```

### Notes

- `sizeof` is a compile-time operator, so it determines the size of types and variables during compilation (except for VLAs).
- When using `sizeof` with arrays, it returns the total size of the array in bytes.
- For pointers, `sizeof` returns the size of the pointer variable, not the size of the data it points to.
