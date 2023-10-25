# Variables

## 1. Data types

Throughout the execution of a script, a lot of data is being manipulated all
the time. This data can be of different types, each serving a different
purpose. The following table lists the data types available in XS and their
corresponding keywords.

| Data type | Keyword        | Possible values                                                                                | Example                       |
| :-------- | :------------- | :--------------------------------------------------------------------------------------------- | :---------------------------- |
| Boolean   | `#!cpp bool`   | `#!cpp true` or `#!cpp false`                                                                  | `#!cpp true`                  |
| Integer   | `#!cpp int`    | Any whole number between `#!cpp -999999999` and `#!cpp 999999999`                              | `#!cpp 42`                    |
| Float     | `#!cpp float`  | Any real number between `#!cpp -999999999.999999` and `#!cpp 999999999.999999`                 | `#!cpp 3.141592`              |
| String    | `#!cpp string` | Any sequence of characters enclosed in double quotes `#!cpp "..."`. See [Strings](strings.md). | `#!cpp "Hey there, partner."` |
| Vector    | `#!cpp vector` | See [Vectors](vectors.md).                                                                     | `#!cpp xsVectorSet(0, 0, 0)`  |

## 2. Variables

Variables are used to store data to be retrieved and manipulated later.

### 2.1. Definition

Defining a variable means creating a new variable by giving it a name, a type
and a value. Variables must be defined before they can be used.

!!! note "Syntax of variable definition"

    ```text
    type name = value;
    ```

#### 2.1.1. Type

This can be any of the [data types](#1-data-types) listed above. This
determines what kind of data the variable can store, e.g. a variable of type
`#!cpp int` cannot store a string.

#### 2.1.2. Name

There are a few rules to follow when naming variables:

- Names are case-sensitive, e.g. `foo` and `Foo` are two different names.
- Names can only contain letters, numbers and underscores. Diacritics are not
  allowed.
- Names must start with a letter or an underscore.
- Names cannot be the same as a [keyword](../reference/keywords.md).
- Variables cannot have the same name as a [function](functions.md),
  [rule](rules.md) or [rule group](rules.md#12-group-name).
- Variables cannot have the same name as another variable,
  [constant](#3-constants) or [label](labels.md) in the same
  [scope](variables-scope.md).

#### 2.1.3. Value

This is the data that the variable will store. The value must be of the same
type as the variable.

#### 2.1.4. Examples

!!! example "Some examples of variable definitions"

    ```cpp
    // Used to store the number of infantry units.
    int numInfantry = 0;

    // Default gatherer distribution.
    float foodGathererPercentage = 0.5;
    float woodGathererPercentage = 0.3;
    float goldGathererPercentage = 0.2;

    // Used to store the position of the main base.
    vector mainBaseLocation = xsVectorSet(0, 0, 0);

    // Used to determine whether an attack should be launched.
    bool shouldAttack = false;
    ```

### 2.2. Assignment

Assigning a variable means changing the value of an existing variable. The
variable must have been defined before it can be assigned.

!!! note "Syntax of variable assignment"

    ```text
    name = value;
    ```

#### 2.2.1. Examples

!!! example "Some examples of variable assignments"

    ```cpp
    // ========================================================================
    // Definitions (see the assignments further below).
    // ========================================================================
    int numInfantry = 0;

    float foodGathererPercentage = 0.5;
    float woodGathererPercentage = 0.3;
    float goldGathererPercentage = 0.2;

    vector mainBaseLocation = xsVectorSet(0, 0, 0);

    bool shouldAttack = false;

    // ========================================================================
    // Assignments, i.e. we will change the values of the variables we just
    // defined.
    // ========================================================================

    // We found 10 infantry units.
    numInfantry = 10;

    // We decided to change the gatherer distribution.
    foodGathererPercentage = 0.4;
    woodGathererPercentage = 0.3;
    goldGathererPercentage = 0.3;

    // We found the main base at x=30, y=0, z=30.
    mainBaseLocation = xsVectorSet(30, 0, 30);

    // We decided to attack.
    shouldAttack = true;
    ```

### 2.3. Constants

Constants are variables whose value cannot be changed after they have been
defined. They are defined in the same way as variables, except that the
`#!cpp const` keyword is written before the type.

!!! note "Syntax of constant definition"

    ```text
    const type name = value;
    ```

#### 2.3.1. Examples

!!! example "Some examples of constant definitions"

    ```cpp
    // The number pi is a constant.
    const float pi = 3.141592;

    // The number e is also a constant.
    const float e = 2.718281;

    // The speed of light is a constant.
    const int c = 299792458;
    ```
