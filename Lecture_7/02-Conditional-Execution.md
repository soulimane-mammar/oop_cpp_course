[//]: # (### Conditional Execution Using if...else)

The `if...else` statement in C++ allows for conditional execution, enabling the program to make decisions based on specified conditions. Here's an explanation of `if...else`:

#### Syntax

```cpp
if (condition) {
    // Code block executed if the condition is true
} else {
    // Code block executed if the condition is false
}
```

#### Example

```cpp
int x = 10;

if (x > 5) {
    cout << "x is greater than 5" << endl;
} else {
    cout << "x is less than or equal to 5" << endl;
}
```

#### Explanation

- The `if` statement checks the given `condition`.
- If the condition is `true`, the code block inside the `if` statement is executed.
- If the condition is `false`, the code block inside the `else` statement (optional) is executed.

#### Nested `if...else`

You can also nest `if...else` statements within each other to create more complex decision trees.

#### Example

```cpp
int age = 25;
bool hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        cout << "You can drive!" << endl;
    } else {
        cout << "You are eligible but don't have a license." << endl;
    }
} else {
    cout << "You are not old enough to drive." << endl;
}
```

#### Multiple Conditions with `else if`

The `else if` statement allows checking multiple conditions if the previous ones are false.

#### Example

```cpp
int number = 0;

if (number > 0) {
    cout << "Number is positive" << endl;
} else if (number < 0) {
    cout << "Number is negative" << endl;
} else {
    cout << "Number is zero" << endl;
}
```

#### Considerations

- Use `{}` to define blocks of code for clarity and to avoid unexpected behavior due to missing braces.
- `else` is optional, and an `if` statement can exist without an `else`.
