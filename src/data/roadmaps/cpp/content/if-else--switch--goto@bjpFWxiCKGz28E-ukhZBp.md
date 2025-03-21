# Control Flow Statements: `if-else`, `switch`, and `goto`

## 1. `if-else` Statement (Selection Statement)

The `if-else` statement is used to evaluate boolean expressions in sequence and execute code blocks based on conditions.

### Syntax

```cpp
if (condition0) {
    // Code block 0
}
else if (condition1) {
    // Code block 1
}
else {
    // Default code block
}
```
NOTE: There is no set limit for number of times we can repeat else if.
### Explanation

- The `if` statement checks `condition0`.
  - If `condition0` is `true`, `code block 0` executes, and the rest is skipped.
  - If `condition0` is `false`, the program moves to the `else if` statement.
- The `else if` statement checks `condition1`.
  - If `condition1` is `true`, `code block 1` executes, and the rest is skipped.
  - If `condition1` is `false`, the program moves to the `else` statement.
- The `else` statement executes by default when none of the previous conditions are met.

### Use Case

The following code checks whether the integer variable `z` is positive, negative, or zero:

```cpp
int z = 1;
if (z > 0) {
    cout << "The integer is positive.\n";
}
else if (z < 0) {
    cout << "The integer is negative.\n";
}
else {
    cout << "The integer is 0.\n";
}
```

## 2. `switch` Statement (Selection Statement)

The `switch` statement is used to check a range of constant expressions. It is simialr to a bunch of `else if` statements but for constant expressions.

### Syntax

```cpp
switch(expression) {
    case one:
        // Code block 0
        break;
    case two:
        // Code block 1
        break;
    default:
        // Default code block
}
```
NOTE: There is no set limit for number of times we can repeat case :.
### Explanation

- The `switch` statement evaluates `expression`.
- It checks whether `expression` matches any of the `case` labels.
- If a match is found, the corresponding code block executes.
- The `break` statement prevents fall-through to the next case.
- If no cases match, the `default` block executes.

### Use Case

The `switch` statement is useful when a variable needs to be compared against multiple discrete values. Unlike `if-else`, `switch` avoids repeated evaluations of the same expression, making it more efficient in some cases.

The following code checks whether the integer variable `z` is 1, 2, or 3:

```cpp
int z = 1;
switch(z) {
    case 1:
        cout << "The integer is 1.\n";
        break;
    case 2:
        cout << "The integer is 2.\n";
        break;
    case 3:
        cout << "The integer is 3.\n";
        break;
    default:
        cout << "The integer is not 1, 2, or 3.\n";
}
```

- If `z = 1`, the `case 1:` block executes, printing "The integer is 1." and breaking out of the `switch`.
- If `z = 2`, the `case 2:` block executes, printing "The integer is 2.".
- If `z = 3`, the `case 3:` block executes, printing "The integer is 3.".
- If `z` is any other value, the `default` block executes, printing "The integer is not 1, 2, or 3.".

## 3. `goto` Statement (Jump Statement)

The `goto` statement is used to jump from one point in the program to another. It should generally be avoided unless it provides a significant benefit, as it can lead to unstructured and hard-to-maintain code.

### Syntax

```cpp
goto label;

label:
    // Code block
```

### Explanation

- To use a `goto` statement, define a `label` to which execution will jump.
- The label is written as a name followed by a colon (`:`), e.g., `myLabel:`.
- When the `goto myLabel;` statement executes, program control jumps to `myLabel:` and continues from there.

### Use Case

The `goto` statement can be useful for breaking out of deeply nested loops or handling specific error conditions.

The following code demonstrates using `goto` to break out of nested loops (this is dumb. Use `return` or `break`):

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            if (i == 2 && j == 2) {
                goto exitLoop;
            }
            cout << "i: " << i << ", j: " << j << endl;
        }
    }

exitLoop:
    cout << "Exited loop." << endl;
    return 0;
}
```
NOTE: Generally avoid this unless necessary.
- The program iterates over two nested loops.
- When `i == 2 && j == 2`, it jumps to `exitLoop:`.
- The `exitLoop:` label terminates the loops and prints "Exited loop.".
- This avoids using additional flags or multiple `break` statements.


