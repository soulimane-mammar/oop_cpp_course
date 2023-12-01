[//]: # (### Getting Code to Execute in Loops)

#### Rudimentary Loops Using `goto`

`goto` statements in C++ allow unconditional jumps from one part of the code to another. While not commonly used for loops due to readability and maintainability concerns, they can be used to create rudimentary loops.

Here's an example demonstrating how `goto` can be utilized for a basic loop-like behavior:

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;
    
loopStart:
    if (i <= 5) {
        cout << i << " ";
        i++;
        goto loopStart; // Jump back to loopStart label
    }
    
    cout << endl << "Loop ended using goto." << endl;
    return 0;
}
```

##### Explanation

- The `goto` statement jumps unconditionally to the label `loopStart`.
- The `if` condition checks if `i` is less than or equal to `5`.
- If the condition is true, it prints the value of `i`, increments `i`, and jumps back to `loopStart`.
- This process continues until `i` becomes greater than `5`, after which the loop ends.

##### Considerations

- Overusing `goto` can make code hard to follow and maintain.
- Loops created using `goto` might lack the clear structure and readability of traditional loops (`for`, `while`, `do-while`).

The use of `goto` for loop-like constructs is discouraged in modern C++ programming due to its potential to complicate code flow and decrease readability. Using structured loop statements (`for`, `while`, `do-while`) is typically preferred for better code organization and understanding.

#### The `while` Loop

The `while` loop in C++ allows for repetitive execution of a block of code as long as a specified condition is true. Here's an explanation of the `while` loop:

##### Syntax

```cpp
while (condition) {
    // Code block to be executed as long as the condition is true
}
```

##### Example

```cpp
int count = 1;

while (count <= 5) {
    cout << count << " ";
    count++;
}

// Output: 1 2 3 4 5
```

##### Explanation

- The `condition` is evaluated before each iteration of the loop.
- If the condition is `true`, the code block inside the `while` loop is executed.
- After each iteration, the condition is checked again.
- When the condition becomes `false`, the loop terminates, and the program continues with the code after the loop.

##### Infinite `while` Loop

```cpp
// An example of an infinite while loop
while (true) {
    // Code block
}
```

##### Use Cases

- Use `while` loops when the number of iterations is not predetermined, and the loop continues until a specific condition becomes false.
- It's suitable when you want to perform an action until a certain condition is met.

##### Considerations

- Ensure that the loop condition can eventually become `false` to prevent infinite loops.
- Always include code that modifies the loop control variable to avoid infinite loops unintentionally.

#### The `do...while` Loop

The `do...while` loop in C++ is a control flow statement that executes a block of code at least once, and then repeatedly executes the block as long as a specified condition is true. Here's an explanation of the `do...while` loop:

##### Syntax

```cpp
do {
    // Code block to be executed at least once
} while (condition);
```

##### Example

```cpp
int count = 1;

do {
    cout << count << " ";
    count++;
} while (count <= 5);

// Output: 1 2 3 4 5
```

##### Explanation

- The code block within the `do` statement is executed first, regardless of the condition.
- After the code block executes, the loop checks the `condition`.
- If the condition is `true`, the loop continues to execute.
- If the condition is `false`, the loop terminates, and the program moves to the code after the loop.

##### Use Cases

- Use `do...while` loops when you want to execute a block of code at least once, regardless of the condition.
- It's suitable for scenarios where the loop must run at least once, such as input validation.

##### Example of Input Validation

```cpp
int userInput;

do {
    cout << "Enter a number between 1 and 10: ";
    cin >> userInput;
} while (userInput < 1 || userInput > 10);
```

##### Considerations

- Ensure that the loop's condition can eventually become `false` to avoid infinite loops.
- Always include code that modifies the loop control variable within the loop block.

#### The `for` Loop

The `for` loop in C++ is a versatile control flow statement used for iterating a specific number of times. It consists of three main components: initialization, condition, and increment/decrement. Here's an explanation of the `for` loop:

##### Syntax

```cpp
for (initialization; condition; increment/decrement) {
    // Code block to be executed in each iteration
}
```

##### Example

```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}

// Output: 1 2 3 4 5
```

##### Explanation

- The `initialization` initializes the loop control variable.
- The `condition` is evaluated before each iteration. If true, the loop continues; otherwise, it exits.
- The `increment/decrement` statement modifies the loop control variable after each iteration.
- The loop executes the code block as long as the `condition` remains true.

##### Components of the `for` Loop

- **Initialization:** Sets the loop control variable's initial value.
- **Condition:** Checks whether the loop should continue iterating.
- **Increment/Decrement:** Modifies the loop control variable to eventually make the condition false.

##### Use Cases

- Use `for` loops when the number of iterations is known or can be determined beforehand.
- Ideal for iterating over arrays, performing calculations, or executing a fixed number of times.

##### Example of Iterating an Array

```cpp
int arr[] = {10, 20, 30, 40, 50};

for (int i = 0; i < 5; i++) {
    cout << arr[i] << " ";
}

// Output: 10 20 30 40 50
```

##### Considerations

- Ensure the loop control variable initialization, condition, and increment/decrement are properly defined to avoid infinite loops.
- The loop control variable's scope is limited to the `for` loop block.

#### The Range-Based `for` Loop

The range-based `for` loop in C++11 and later versions provides a convenient way to iterate through elements in a range, such as arrays, containers, or sequences, without explicitly managing loop control variables or indices. Here's an explanation of the range-based `for` loop:

##### Syntax

```cpp
for (type var : range) {
    // Code block to be executed for each element in the range
}
```

##### Example with Array

```cpp
int arr[] = {1, 2, 3, 4, 5};

for (int num : arr) {
    cout << num << " ";
}

// Output: 1 2 3 4 5
```

##### Example with Vector (Container)

```cpp
#include <vector>
using namespace std;

vector<int> vec = {10, 20, 30, 40, 50};

for (int value : vec) {
    cout << value << " ";
}

// Output: 10 20 30 40 50
```

##### Explanation

- The range-based `for` loop iterates over each element in the specified range.
- `type` represents the data type of elements in the range.
- `var` is a variable that holds the value of each element in the iteration.
- `range` can be an array, container, initializer list, or any range-based expression.

##### Use Cases

- Use the range-based `for` loop when iterating through the entire elements of arrays, containers, or sequences.
- Ideal for enhancing readability and simplicity in code, especially when the loop control variable or index isn't required.

##### Considerations

- The loop variable `var` is a copy of the elements in the range, not a reference. To modify elements, use a reference variable (`type& var`).
