# Loops

Loops are used when you want to repeat a block of code multiple times. There are
two types of loops in XS: `#!cpp while` loops and `#!cpp for` loops.

## 1. `#!cpp while` loops

The `#!cpp while` loop is used to execute a block of code while a condition is
met. The condition is checked at the beginning of each iteration of the loop.

!!! note "Syntax of a `#!cpp while` loop"

    ```cpp
    while (condition)
    {
        // code to execute while condition is true
    }
    ```

### 1.1. Example

!!! example "Example of a `#!cpp while` loop"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        // Set the seed of the random number generator.
        aiRandSetSeed(-1);

        // Keep generating random numbers until we get one that is less than 2
        int numAttempts = 0;
        while(aiRandInt(10) >= 2)
        {
            numAttempts++;
            aiEcho("The generated number is greater than or equal to 2 (attempt #" + numAttempts + "). Trying again...");
        }

        aiEcho("" + numAttempts + " random numbers were generated before we got one that was less than 2.");
    }
    ```

## 2. `#!cpp for` loops

The `#!cpp for` loop is primarily used to execute a block of code a certain
number of times. For that, it uses a counter variable that is incremented or
decremented at the end of each iteration of the loop.

!!! note "Syntax of a `#!cpp for` loop"

    ```cpp
    for (initialization; condition; increment)
    {
        // code to execute while condition is true
    }
    ```

### 2.1. Initialization

This is where you initialize the counter variable. It is only executed once,
before the first iteration of the loop.

### 2.2. Condition

This is where you specify the condition that must be met for the loop to
proceed. It is checked at the beginning of each iteration of the loop. Once the
condition is no longer met, the loop stops.

### 2.3. Increment

This is where you specify how the counter variable should be incremented or
decremented at the end of each iteration of the loop.

### 2.4. Example

!!! example "Example of a `#!cpp for` loop"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        // Set the seed of the random number generator.
        aiRandSetSeed(-1);

        // Generate 10 random numbers and print them to the console
        for (int i = 0; i < 10; i++)
        {
            aiEcho("Random number #" + (i + 1) + ": " + aiRandInt(10));
        }
    }
    ```

## 3. `#!cpp break` statement

The `#!cpp break` statement is used to exit a loop even if the condition is
still met.

!!! example "Example of a `#!cpp break` statement"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        // Set the seed of the random number generator.
        aiRandSetSeed(-1);

        // Keep generating random numbers until we get one that is less than 2
        int numAttempts = 0;
        while(true)
        {
            numAttempts++;
            int randNum = aiRandInt(10);
            aiEcho("The generated number is " + randNum + " (attempt #" + numAttempts + ").");

            if (randNum < 2)
            {
                break;
            }
        }

        aiEcho("" + numAttempts + " random numbers were generated before we got one that was less than 2.");
    }
    ```

## 4. `#!cpp continue` statement

The `#!cpp continue` statement is used to skip the rest of the code in the
current iteration of the loop and proceed to the next iteration.

!!! example "Example of a `#!cpp continue` statement"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        // Set the seed of the random number generator.
        aiRandSetSeed(-1);

        // Generate 10 random numbers and print them to the console
        for (int i = 0; i < 10; i++)
        {
            int randNum = aiRandInt(10);

            if (randNum < 2)
            {
                aiEcho("Skipping random number #" + (i + 1) + " because it is less than 2.");
                continue;
            }

            aiEcho("Random number #" + (i + 1) + ": " + randNum);
        }
    }
    ```
