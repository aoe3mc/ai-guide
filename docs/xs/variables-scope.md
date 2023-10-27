# Variables Scope

Variable scope refers to the region of script from where a variable can be
accessed. There are a few different scopes in XS:

- File scope.
- Global scope.
- Local scope.

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

### Lifetime

File-scoped variables keep their values between function calls:

!!! example "Lifetime of file-scoped variables."

    ```text title="Structure of the AI folder"
    ├── Age3AI.xs
    ├── file-scope-test.xs
    ```

    ```cpp title="file-scope-test.xs"
    // In the beginning, the value of foo is 0.
    int foo = 0;

    void function1(void)
    {
        // When this function is called, the value of foo
        // becomes -1.
        foo = -1;
    }

    void function2(void)
    {
        // When this function is called, the value of foo
        // becomes 10;
        foo = 10;
    }

    void echoFoo(void)
    {
        aiEcho("foo = " + foo);
    }
    ```

    ```cpp title="Age3AI.xs"
    include "./file-scope-test.xs";

    void main(void)
    {
        echoFoo();
        function1();
        echoFoo();
        function2();
        echoFoo();
    }
    ```

## 2. Global Scope

Variables defined in a file, outside of any function or rule, and marked with
the `#!cpp extern` keyword, are global scoped. They can be accessed from
any function or rule in any file where the file containing the variable is
included, provided that such function or rule is defined after the variable's
definition.

These variables are commonly referred to as **global variables**.

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

### Lifetime

Like file-scoped variables, global variables also keep their values between
function calls.

## 3. Local Scope

Variables defined inside a function are local to that function. They can only be
accessed from within that function.

These variables are commonly referred to as **local variables**.

There are two types of local variables:

- non-`#!cpp static` variables
- `#!cpp static` variables

### 3.1. Non-`#!cpp static` variables

!!! example "Non-`#!cpp static` local variable."

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

#### Lifetime

Non-static variables lose their values between function calls.

!!! example "Lifetime of non-`#!cpp static` local variables."

    ```cpp title="Age3AI.xs"
    void lifetimeTest(void)
    {
        int foo = 0;

        aiEcho("foo = " + foo);

        foo = aiRandInt(10);
    }

    void main(void)
    {
        aiRandSetSeed(-1);
        lifetimeTest();
        lifetimeTest();
        lifetimeTest();
    }
    ```

### 3.2. `#!cpp static` variables

These variables are marked with the `#!cpp static` keyword. They keep their
values between function calls.

!!! example "Lifetime of `#!cpp static` local variables."

    ```cpp title="Age3AI.xs"
    void lifetimeTest(void)
    {
        static int foo = 0;

        aiEcho("foo = " + foo);

        foo = aiRandInt(10);
    }

    void main(void)
    {
        aiRandSetSeed(-1);
        lifetimeTest();
        lifetimeTest();
        lifetimeTest();
    }
    ```
