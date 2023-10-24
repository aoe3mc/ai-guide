# Variables Scope

Variable scope refers to the region of script from where a variable can be
accessed. There are a few different scopes in XS:

- File scope.
- Global scope.
- Function scope.

## 1. File Scope

Variables defined in a file, outside of any function or rule, are file scoped.
They can be accessed from any function or rule in the same file, provided that
such function or rule is defined after the variable's definition. They cannot
be accessed from any other file.

!!! example "File scoped variables."

    ```text title="Structure of the AI folder"
    ├── Age3AI.xs
    ├── file-scope-test.xs
    ```

    ```cpp title="file-scope-test.xs"
    int foo = 0;

    void scopeTest(void)
    {
        // foo is accessible here.
        foo = 10;
    }
    ```

    ```cpp title="Age3AI.xs"
    include "./file-scope-test.xs";

    void main(void)
    {
        // foo cannot be accessed here.
        foo = 20; // This will cause an error.
    }
    ```

## 2. Global Scope

Variables defined in a file, outside of any function or rule, and marked with
the `#!cpp extern` keyword, are global scoped. They can be accessed from
any function or rule in any file where the file containing the variable is
included, provided that such function or rule is defined after the variable's
definition.

!!! example "Global scoped variables."

    ```text title="Structure of the AI folder"
    ├── Age3AI.xs
    ├── global-scope-test.xs
    ```

    ```cpp title="global-scope-test.xs"
    extern int foo = 0;

    void scopeTest(void)
    {
        // foo is accessible here.
        foo = 10;
    }
    ```

    ```cpp title="Age3AI.xs"
    include "./global-scope-test.xs";

    void main(void)
    {
        // foo is accessible here.
        foo = 20;
    }
    ```

## 3. Function Scope

Variables defined inside a function are function scoped. They can only be
accessed from within the function.

!!! example "Function scoped variables."

    ```cpp title="Age3AI.xs"
    void scopeTest(void)
    {
        int foo = 0;

        // foo is accessible here.
        foo = 10;
    }

    void main(void)
    {
        // foo cannot be accessed here.
        foo = 20; // This will cause an error.
    }
    ```
