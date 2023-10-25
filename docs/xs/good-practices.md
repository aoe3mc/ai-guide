# Good Practices

To make it easier to maintain your code and collaborate on your scripts, you
are highly recommended to adhere to the following guidelines.

## 1. Indentation and formatting

In a script, a whitespace is one or more spaces, tabs or newlines, or any
combination of these. Whitespace is used to separate tokens
([keywords](../reference/keywords.md), [operators](operators.md),
identifiers, i.e. variable names, function names, etc.) from each other.

The game only needs one space between tokens (or no whitespace at all in some
cases). Which means that you can write your code like this:

!!! example "Bad code formatting"

    ```cpp title="Age3AI.xs"
    void main(void) { aiEcho("Hello, world!"); }
    ```

However, this is not very readable. To make your code more readable, you should
use **indentation** and **line breaks** to separate statements and blocks of
code.

!!! example "Good code formatting"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        aiEcho("Hello, world!");
    }
    ```

Indentation is the process of adding whitespace at the beginning of a line to
make it stand out from the rest of the code. In the example above, the line
`#!cpp aiEcho("Hello, world!");` is indented with four spaces.

In general, you indent the code each time you open a new block of code (like an
`#!cpp if` statement or a function body). You can use tabs or spaces for
indentation, but you should be consistent and use the same style throughout your
script.

!!! example "Another example"

    Here, the `#!cpp if` statement opens a new block of code, so the code inside
    is indented. Same for `#!cpp else`.

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        aiRandSetSeed(-1);
        if (aiRandInt(100) < 50)
        {
            aiEcho("Let it begin!");
        }
        else
        {
            aiEcho("Let's get it on!");
        }
    }
    ```

## 2. Comments

- Comments should be concise and to the point.
- Don't abuse comments. In general, you should only use comments to explain
  complex code or to provide additional information that is not obvious from the
  code itself.

## 3. Naming

As a general rule, you should use descriptive names for your variables,
functions, etc. This makes it easier to understand what they do and what they
are used for.

There are also more specific conventions:

- [Global variables](variables-scope.md#2-global-scope) are usually prefixed
  with `g` (e.g. `gForwardBaseID`). This is to make it clear that they are
  global.
- [Local variables](variables-scope.md#3-function-scope) are usually written in
  [camel case](https://en.wikipedia.org/wiki/Camel_case) where the first letter
  is lowercase (e.g. `forwardBaseID`).
- [Constants](variables.md#23-constants) are usually prefixed with `c` (e.g.
  `cMaxSettlersPerFarm`). This is to make it clear that they are constants.
- [Functions](functions.md) are usually written in camel case where the first
  letter is lowercase (e.g. `getUnit`).
- [Rules](rules.md) are usually written in camel case where the first letter is
  uppercase (e.g. `ManageGatherers`).
- There is no definitive convention for [rule groups](rules.md#12-group-name).
  However, the default AI scripts use camel case where the first letter is
  lowercase (e.g. `tcComplete`).
- There is no definitive convention for [labels](labels.md) either. In fact,
  labels are rarely used in AI scripts.

!!! tip "You can make your own naming conventions"

    It is definitely possible that you don't like the conventions described
    above. You can make your own conventions as long as you are consistent and
    you document them in your script.

    ??? example "[This example](https://github.com/thinotmandresy/impmod-aai/blob/main/aai/build.xs) uses the following conventions:"

        - Global variables are prefixed with `g` (e.g. `gUnitTypeHouse`).
        - Local variables are written in [snake
        case](https://en.wikipedia.org/wiki/Snake_case) (e.g. `house_build_plan`).
        - Constants are prefixed with `c` (e.g. `cStrategyBoom`).
        - Functions are written in camel case with the first letter being lowercase
        (e.g. `getUnit1`).
        - Rules are written in camel case with the first letter being uppercase (e.g.
        `MaintainHouses`).
        - Rule groups are prefixed with `rg` (e.g. `rgMainBase`).
