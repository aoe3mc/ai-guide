# Conditionals

Conditionals are used when you want to execute a block of code only if a
certain condition is met.

## 1. `#!cpp if` statement

The `#!cpp if` statement is used to execute a block of code only if a
certain condition is met.

!!! note "Syntax of an `#!cpp if` statement"

    ```cpp
    if (condition)
    {
        // code to execute if condition is true
    }
    ```

### 1.1. Example

!!! example "Example of an `#!cpp if` statement"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        // Set the seed of the random number generator.
        aiRandSetSeed(-1);

        // Generate a random number between 0 and 9
        int randomNumber = aiRandInt(10);

        // Say hello only if the random number is less than 7
        if (randomNumber < 7)
        {
            aiEcho("Hello!");
        }
    }
    ```

    !!! tip "You can keep restarting the scenario to see the different outcomes."

        If the **AI Debug Output** does not print anything, it means that the
        random number was greater than or equal to 7. Otherwise you should see
        the following output:

        ```text title="AI Debug Output"
        00:00:00 (0): P#1 (Player 1) Hello!
        ```

## 2. `#!cpp if-else` statement

The `#!cpp if-else` statement is used to execute a block of code if a
condition is met, and another block of code if the condition is not met.

!!! note "Syntax of an `#!cpp if-else` statement"

    ```cpp
    if (condition)
    {
        // code to execute if condition is true
    }
    else
    {
        // code to execute if condition is false
    }
    ```

### 2.1. Example

!!! example "Example of an `#!cpp if-else` statement"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        // Set the seed of the random number generator.
        aiRandSetSeed(-1);

        // Generate a random number between 0 and 9
        int randomNumber = aiRandInt(10);

        if (randomNumber < 5)
        {
            aiEcho("The random number is less than 5 (it is " + randomNumber + ")");
        }
        else
        {
            aiEcho("The random number is greater than or equal to 5 (it is " + randomNumber + ")");
        }
    }
    ```

## 3. `#!cpp if-else if-else` statement

It is possible to chain multiple `#!cpp if-else` statements together to
execute different blocks of code depending on the value of a variable.

!!! note "Syntax of an `#!cpp if-else if-else` statement"

    ```cpp
    if (condition1)
    {
        // code to execute if condition1 is true
    }
    else if (condition2)
    {
        // code to execute if condition1 is false and condition2 is true
    }
    // (you can add as many "else if" statements as you want)
    else
    {
        // code to execute if all conditions are false
    }
    ```
