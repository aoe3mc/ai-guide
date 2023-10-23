# Strings

Strings represent text. Most of the time, they are used for debugging purposes.

## 1. Creating a string

Strings are created by enclosing text in double quotes:

!!! example "Example of a string"

    ```cpp
    "Hey there, partner."
    ```

## 2. String concatenation

### 2.1. Concatenating two strings

Strings can be concatenated using the `+` operator:

!!! example "Example of string concatenation"

    ```cpp
    "Hello" + " " + "world!" // "Hello world!"
    ```

### 2.2. Concatenating a string and another value

A string can be concatenated with a value of any type. The value will be
converted to a string.

!!! example "Example of string concatenation with another value"

    ```cpp
    "I found " + 3 + " apples." // "I found 3 apples."
    ```

It makes more sense when the value is a variable:

!!! example "Example of string concatenation with a variable"

    ```cpp
    int diceRoll = 1 + aiRandInt(6); // 1-6
    aiEcho("You rolled a " + diceRoll + ".");
    ```

## 3. Escape sequences

Certain characters cannot be used directly in a string. For example, since the
double quote character is used to delimit strings, it cannot be used directly
inside a string. To use such characters, you must use an escape sequence.

An escape sequence is a backslash (`\`) followed by a character. The backslash
tells the game that the character that follows is special and should be treated
differently.

Here's a list of the most frequently used escape sequences:

| Escape sequence | Character    | Example              | Result                        |
| --------------- | ------------ | -------------------- | ----------------------------- |
| `#!cpp \n`      | Newline      | `#!cpp "Hello\nworld!"`    | `Hello`<br>`world!`           |
| `#!cpp \t`      | Tab          | `#!cpp "Hello\tworld!"`    | Cannot be shown in this table |
| `#!cpp \"`      | Double quote | `#!cpp "Hello \"world\"!"` | `Hello "world"!`              |
| `#!cpp \\`      | Backslash    | `#!cpp "Hello \\world!"`   | `Hello \world!`               |
