[//]:# (### Recursion: Functions That Invoke Themselves)

Recursion is a programming technique where a function calls itself directly or indirectly to solve a problem by breaking it down into smaller instances of the same problem. In recursion, there's a base case that defines the terminating condition, and there are recursive cases where the function calls itself with modified arguments to converge towards the base case.

Here's an example of a simple recursive function to calculate the factorial of a number:

```cpp
#include <iostream>

// Recursive function to calculate factorial
unsigned int factorial(unsigned int n) {
    if (n == 0 || n == 1) {
        return 1; // Base case: factorial of 0 and 1 is 1
    } else {
        return n * factorial(n - 1); // Recursive case: n * factorial(n-1)
    }
}

int main() {
    int number = 5;
    std::cout << "Factorial of " << number << " is: " << factorial(number) << std::endl;
    return 0;
}
```

In this example, the `factorial` function is defined to calculate the factorial of a non-negative integer `n`. The base case is when `n` equals 0 or 1, where the factorial is 1. For any other value of `n`, it calls itself with `factorial(n - 1)` until it reaches the base case.

When `factorial(5)` is called in `main()`, it executes as follows:

- `factorial(5)` calls `5 * factorial(4)`
- `factorial(4)` calls `4 * factorial(3)`
- `factorial(3)` calls `3 * factorial(2)`
- `factorial(2)` calls `2 * factorial(1)`
- `factorial(1)` reaches the base case and returns 1
- The subsequent multiplications are performed to calculate the final result: 5 *4* 3 *2* 1 = 120

Recursion is a powerful technique but requires careful handling of base cases to prevent infinite recursion. It's commonly used for problems that can be broken down into smaller, similar sub-problems.
