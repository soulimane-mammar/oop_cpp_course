[//]: # (### Statements)

Statements in C++ are individual instructions that make up a program. They can perform actions, control program flow, or define behavior within a program. Here are several types of statements commonly used in C++:

#### 1. **Expression Statements:**

- Evaluate an expression and terminate it with a semicolon.

   ```cpp
   int x = 5;  // Expression statement: assigns 5 to variable x
   ```

#### 2. **Declaration Statements:**

- Declare variables or functions.

   ```cpp
   int y;  // Declaration statement: declares an integer variable y
   ```

#### 3. **Control Flow Statements:**

- **Conditional Statements (`if`, `else`, `switch`):**

     ```cpp
     if (condition) {
         // Code executed if condition is true
     } else {
         // Code executed if condition is false
     }
     ```

- **Looping Statements (`for`, `while`, `do-while`):**

     ```cpp
     for (int i = 0; i < 5; ++i) {
         // Code executed in a loop
     }
     ```

- **Jump Statements (`break`, `continue`, `return`, `goto`):**

     ```cpp
     return 0;  // Return statement: ends a function and returns a value
     ```

#### 4. **Compound Statements (Blocks):**

- A block of statements enclosed within curly braces `{}`.

   ```cpp
   {
       // Multiple statements grouped as a single block
   }
   ```

#### 5. **Null Statement:**

- An empty statement represented by a semicolon, indicating no action.

   ```cpp
   ; // Null statement: does nothing
   ```

Each statement serves a specific purpose and contributes to the overall functionality and behavior of a C++ program, allowing developers to control the flow of execution, perform actions, and manage program state.
