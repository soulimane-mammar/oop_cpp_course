[//]: # (### Operator Precedence and Associativity)

In C++, operator precedence and associativity define the order in which different operators are evaluated within an expression. Operator precedence determines which operators are evaluated first, while associativity defines the order when operators of the same precedence level appear together.

#### Operator Precedence

- **Higher precedence:** Operators with higher precedence are evaluated before those with lower precedence.
- **Parentheses:** Operations within parentheses have the highest precedence.
- **Examples:** Multiplication (`*`) and division (`/`) have higher precedence than addition (`+`) and subtraction (`-`).

#### Operator Associativity

- **Left-to-right:** Operators with left-to-right associativity are evaluated from left to right when they have the same precedence.
- **Right-to-left:** Operators with right-to-left associativity are evaluated from right to left when they have the same precedence.
- **Examples:** Assignment (`=`) and most binary operators have left-to-right associativity. Unary operators like increment/decrement (`++`, `--`) have right-to-left associativity.

#### Example

```cpp
int result = 5 + 2 * 3;  // Multiplication has higher precedence than addition

// Evaluation: 2 * 3 = 6, then 5 + 6 = 11
```

#### Explicit Use of Parentheses

- Parentheses can be used to override the default precedence and enforce a specific evaluation order.
- They can also enhance code readability and avoid ambiguity.

```cpp
int result = (5 + 2) * 3;  // Forces addition before multiplication
// Evaluation: 5 + 2 = 7, then 7 * 3 = 21
```

#### Operator Precedence and Associativity Table

Here's a table that outlines the operator precedence in C++, from highest to lowest precedence. Operators within the same box have equal precedence and generally associate left to right.

| Precedence | Operator(s)                                                                                                                                                                                                                                                                                                                 |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Highest    | :: (scope resolution)<br> () (function call)<br> [] (array subscripting)<br> .  (member access)<br> -> (member access through pointer)<br> ++ (postfix), -- (postfix)<br>                                                                                                                                                   |
|            | ++ (prefix), -- (prefix)<br> + (unary), - (unary), ! (logical NOT), ~ (bitwise NOT)<br> *(dereference), & (address-of), sizeof, type cast <br> new, new[], delete, delete[], dynamic_cast, static_cast, reinterpret_cast, const_cast<br> .* (pointer to member access), ->* (pointer to member access through pointer)<br> |
|            | *, /, %                                                                                                                                                                                                                                                                                                                     |
|            | +, -                                                                                                                                                                                                                                                                                                                        |
|            | <<, >>                                                                                                                                                                                                                                                                                                                      |
|            | <, <=, >, >=                                                                                                                                                                                                                                                                                                                |
|            | ==, !=                                                                                                                                                                                                                                                                                                                      |
|            | & (bitwise AND)                                                                                                                                                                                                                                                                                                             |
|            | ^ (bitwise XOR)                                                                                                                                                                                                                                                                                                             |
|            | \| (bitwise OR)                                                                                                                                                                                                                                                                                                             |
|            | && (logical AND)                                                                                                                                                                                                                                                                                                            |
|            | \|\| (logical OR)                                                                                                                                                                                                                                                                                                           |
|            | ? : (conditional)                                                                                                                                                                                                                                                                                                           |
|            | =, +=, -=, *=, /=, %=, &=, \|=, ^=, <<=, >>= (assignment operators)                                                                                                                                                                                                                                                         |
| Lowest     | , (comma operator - least precedence)                                                                                                                                                                                                                                                                                       |
