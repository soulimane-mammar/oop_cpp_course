[//]: #  (### Modifying Loop Behavior Using continue and break)

In C++, the `break` and `continue` statements alter the behavior of loops—`break` terminates the loop prematurely, while `continue` skips the current iteration and moves to the next iteration.

#### `break` Statement

The `break` statement is used to exit the loop prematurely when a certain condition is met.

##### Example

```cpp
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        break; // Exit the loop when i becomes 3
    }
    cout << i << " ";
}

// Output: 1 2
```

##### Explanation

- In this example, the loop prints numbers from 1 to 5.
- The `if` condition checks if `i` is equal to `3`.
- When `i` becomes `3`, the `break` statement terminates the loop immediately.

#### `continue` Statement

The `continue` statement is used to skip the current iteration and proceed to the next iteration of the loop.

##### Example

```cpp
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue; // Skip printing 3
    }
    cout << i << " ";
}

// Output: 1 2 4 5
```

##### Explanation

- In this example, the loop prints numbers from 1 to 5.
- When `i` equals `3`, the `continue` statement skips the code inside the loop for that iteration, moving to the next iteration.

##### Use Cases

- `break` is useful for exiting loops prematurely based on specific conditions.
- `continue` is helpful for skipping specific iterations and continuing with the next iteration of the loop.
