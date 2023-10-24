# Functions

Functions are used to group together multiple statements into a single block of
code that can be executed multiple times. The use of functions helps to reduce
code duplication and makes the code easier to read and maintain.

## 1. Definition

Defining a function means creating a new function by giving it a name, a return
type, a list of parameters and a body. Functions must be defined before they can
be used.

!!! note "Syntax of function definition"

    ```text
    returnType name(parameters)
    {
        // body
        return(returnValue);
    }
    ```

### 1.1. Return type

This can be any of the [data types](variables.md#1-data-types) listed in the
section about variables. This determines what kind of data the function will
return, e.g. a function with return type `#!cpp int` cannot return a string.
If the function does not return anything, the return type should be `#!cpp void`.

### 1.2. Name

Function names follow the same rules as [variable names](variables.md#212-name):

- Names are case-sensitive, e.g. `foo` and `Foo` are two different names.
- Names can only contain letters, numbers and underscores. Diacritics are not
  allowed.
- Names must start with a letter or an underscore.
- Names cannot be the same as a [keyword](../reference/keywords.md).
- Functions cannot have the same name as a [variable](variables.md), constant,
  [rule](rules.md), [rule group](rules.md#12-group-name) or another function.

### 1.3. Parameters

Parameters are used to pass data to the function. They have the same syntax as
[variable definitions](variables.md#21-definition) without the semicolon at the
end. Multiple parameters are separated by commas.

### 1.4. Body

The body of the function is a block of code that will be executed when the
function is called. It can contain any number of statements. However, there
are some restrictions:

- You cannot define a function inside another function.
- You cannot define a [rule](rules.md) inside a function.

### 1.5. Return value

The return value is the data that the function will return. It must be of the
same type as the function's return type. If the function does not return
anything, the return value should be omitted.

### 1.6. Examples

!!! example "Examples of function definition"

    ```cpp title="Age3AI.xs"
    int factorial(int n = 0)
    {
        // Factorial of 0 is 1.
        if (n == 0)
        {
            return(1);
        }

        // Calculate the factorial.
        int result = 1;
        for (int i = 1; i <= n; i++)
        {
            result *= i;
        }

        return(result);
    }
    ```

## 2. Calling

Calling a function means executing the code inside the function's body. This is
done by using the function's name followed by a list of arguments in parentheses.

!!! note "Syntax of function call"

    ```text
    name(arguments);
    ```

### 2.1. Arguments

The arguments are the data that will be passed to the function. They must be of
the same type as the function's parameters. Multiple arguments are separated by
commas.

### 2.2. Examples

!!! example "Some examples of function calls"

    ```cpp title="Age3AI.xs"
    // (see the definition of the factorial function above)

    void main(void)
    {
        // Set the seed of the random number generator.
        aiRandSetSeed(-1);

        // Generate some random numbers and print their factorials.
        for (int i = 0; i < 10; i++)
        {
            int n = aiRandInt(0, 10);
            int f = factorial(n);
            aiEcho("Factorial of " + n + " is " + f);
        }
    }
    ```

!!! question "Where is the definition of the `aiEcho` function?"

    `aiEcho` is a [built-in function](../reference/functions/ai.md), which means
    that it is defined in the game engine.
