# Operators

Operators are used to perform operations on variables and constants. This
section talks about the most frequently used operators in XS.

## 1. Arithmetic operators

| Operator  | Expression    | Description                                                 | Example       | Result    |
| --------- | ------------- | ----------------------------------------------------------- | ------------- | --------- |
| `#!cpp +` | `#!cpp a + b` | Adds `#!cpp a` and `#!cpp b`.                               | `#!cpp 2 + 3` | `#!cpp 5` |
| `#!cpp -` | `#!cpp a - b` | Subtracts `#!cpp b` from `#!cpp a`.                         | `#!cpp 5 - 3` | `#!cpp 2` |
| `#!cpp *` | `#!cpp a * b` | Multiplies `#!cpp a` by `#!cpp b`.                          | `#!cpp 2 * 3` | `#!cpp 6` |
| `#!cpp /` | `#!cpp a / b` | Divides `#!cpp a` by `#!cpp b`.                             | `#!cpp 6 / 2` | `#!cpp 3` |
| `#!cpp %` | `#!cpp a % b` | Calculates the remainder of `#!cpp a` divided by `#!cpp b`. | `#!cpp 5 % 2` | `#!cpp 1` |

## 2. Comparison operators

| Operator   | Expression     | Description                                                | Example        | Result        |
| ---------- | -------------- | ---------------------------------------------------------- | -------------- | ------------- |
| `#!cpp ==` | `#!cpp a == b` | Checks if `#!cpp a` is equal to `#!cpp b`.                 | `#!cpp 2 == 3` | `#!cpp false` |
| `#!cpp !=` | `#!cpp a != b` | Checks if `#!cpp a` is not equal to `#!cpp b`.             | `#!cpp 2 != 3` | `#!cpp true`  |
| `#!cpp <`  | `#!cpp a < b`  | Checks if `#!cpp a` is less than `#!cpp b`.                | `#!cpp 2 < 3`  | `#!cpp true`  |
| `#!cpp <=` | `#!cpp a <= b` | Checks if `#!cpp a` is less than or equal to `#!cpp b`.    | `#!cpp 2 <= 3` | `#!cpp true`  |
| `#!cpp >`  | `#!cpp a > b`  | Checks if `#!cpp a` is greater than `#!cpp b`.             | `#!cpp 2 > 3`  | `#!cpp false` |
| `#!cpp >=` | `#!cpp a >= b` | Checks if `#!cpp a` is greater than or equal to `#!cpp b`. | `#!cpp 2 >= 3` | `#!cpp false` |

## 3. Logical operators

| Operator     | Expression                       | Description                                      | Example                                 | Result        |
| ------------ | -------------------------------- | ------------------------------------------------ | --------------------------------------- | ------------- |
| `#!cpp !`    | `#!cpp !a`                       | Turns `#!cpp a` into its opposite.               | `#!cpp !true`                           | `#!cpp false` |
| `#!cpp &&`   | `#!cpp a && b`                   | Checks if `#!cpp a` and `#!cpp b` are both true. | `#!cpp true && false`                   | `#!cpp false` |
| &#124;&#124; | `#!cpp a` &#124;&#124; `#!cpp b` | Checks if `#!cpp a` or `#!cpp b` is true.        | `#!cpp true` &#124;&#124; `#!cpp false` | `#!cpp true`  |

## 4. Assignment operators

Assignment operators involve assigning a value to a variable. The variable to
which the value is assigned is always on the left side of the operator, and
must have been defined before.

| Operator   | Expression     | Description                                                                                       | Example        | Result                                    |
| ---------- | -------------- | ------------------------------------------------------------------------------------------------- | -------------- | ----------------------------------------- |
| `#!cpp =`  | `#!cpp a = b`  | Assigns the value of `#!cpp b` to `#!cpp a`.                                                      | `#!cpp a = 2`  | The value of `#!cpp a` is now `#!cpp 2`   |
| `#!cpp +=` | `#!cpp a += b` | Adds `#!cpp b` to `#!cpp a`, then assigns the result to `#!cpp a`.                                | `#!cpp a += 2` | The value of `#!cpp a` has increased by 2 |
| `#!cpp -=` | `#!cpp a -= b` | Subtracts `#!cpp b` from `#!cpp a`, then assigns the result to `#!cpp a`.                         | `#!cpp a -= 2` | The value of `#!cpp a` has decreased by 2 |
| `#!cpp *=` | `#!cpp a *= b` | Multiplies `#!cpp a` by `#!cpp b`, then assigns the result to `#!cpp a`.                          | `#!cpp a *= 2` | The value of `#!cpp a` has doubled        |
| `#!cpp /=` | `#!cpp a /= b` | Divides `#!cpp a` by `#!cpp b`, then assigns the result to `#!cpp a`.                             | `#!cpp a /= 2` | The value of `#!cpp a` has halved         |
| `#!cpp %=` | `#!cpp a %= b` | Calculates the remainder of `#!cpp a` divided by `#!cpp b`, then assigns the result to `#!cpp a`. | `#!cpp a %= 2` | The value of `#!cpp a` has changed        |

## 5. Increment and decrement operators

Increment and decrement operators are used to increase or decrease the value of
a variable by 1.

| Operator   | Expression  | Description                                                                  | Example     | Result                                    |
| ---------- | ----------- | ---------------------------------------------------------------------------- | ----------- | ----------------------------------------- |
| `#!cpp ++` | `#!cpp a++` | Increases the value of `#!cpp a` by 1, then assigns the result to `#!cpp a`. | `#!cpp a++` | The value of `#!cpp a` has increased by 1 |
| `#!cpp --` | `#!cpp a--` | Decreases the value of `#!cpp a` by 1, then assigns the result to `#!cpp a`. | `#!cpp a--` | The value of `#!cpp a` has decreased by 1 |

## 6. Concatenation operator

The concatenation operator is used to combine two strings into one. It is
represented by the `#!cpp +` symbol. For example, `#!cpp "Hello" + " " + "world"`
will result in the string `#!cpp "Hello world"`.

It is also possible to concatenate a string with any other data type. For
that, the quotation marks are not used. For example, `#!cpp "Hello " + 2` will
result in the string `#!cpp "Hello 2"`.

## 7. Ternary operator

The ternary operator is a special operator that takes three operands. It is
used to shorten an [`#!cpp if` statement](conditionals.md#1-if-statement).

!!! note "Syntax of the ternary operator"

    ```text
    condition ? expression1 : expression2
    ```

    The ternary operator evaluates `condition`. If it is true, it evaluates
    `expression1` and returns its value. Otherwise, it evaluates `expression2`
    and returns its value.

!!! example "Some examples of the ternary operator"

    ```cpp
    // (assuming that all variables have been defined.)

    // Use all settlers to gather wood if we need a town center asap and we
    // don't have enough wood, otherwise use the default distribution.
    int numWoodGatherers = numTCs == 0 && woodAmount < 600 ? numSettlers : numSettlers * woodGathererPercentage;
    ```

## 8. Operator precedence

Operator precedence determines the order in which operators are evaluated. For
example, in the expression `#!cpp 2 + 3 * 4`, the multiplication is evaluated
first, then the addition. This is because the multiplication operator has a
higher precedence than the addition operator.

Operators with a higher precedence are evaluated before operators with a lower
precedence.

| Precedence | Operator(s)                                                           |
| ---------- | --------------------------------------------------------------------- |
| 1          | `#!cpp ++`, `#!cpp --`                                                |
| 2          | `#!cpp !`                                                             |
| 3          | `#!cpp *`, `#!cpp /`, `#!cpp %`                                       |
| 4          | `#!cpp +`, `#!cpp -`                                                  |
| 5          | `#!cpp <`, `#!cpp <=`, `#!cpp >`, `#!cpp >=`                          |
| 6          | `#!cpp ==`, `#!cpp !=`                                                |
| 7          | `#!cpp &&`                                                            |
| 8          | &#124;&#124;                                                          |
| 9          | `#!cpp =`, `#!cpp +=`, `#!cpp -=`, `#!cpp *=`, `#!cpp /=`, `#!cpp %=` |
| 10         | `#!cpp ? :`                                                           |

## 9. Using parentheses

Parentheses can be used to override the default precedence of operators. For
example, in the expression `#!cpp 2 + 3 * 4`, the multiplication is evaluated
first, then the addition. However, if we want the addition to be evaluated
first, we can use parentheses: `#!cpp (2 + 3) * 4`.

Parentheses can be nested, and the expression inside the innermost pair of
parentheses is evaluated first.
