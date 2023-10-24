# Includes

It is possible include the content of a file in another file using the `include`
directive.

!!! note "Syntax of the `include` directive"

    ```cpp
    include "path/to/file.xs";
    ```

In a script, the `include` directive is replaced by the content of the
corresponding file.

!!! example "Example of file inclusion"

    Let's say `foo.xs` contains the following code and is placed in the same
    folder as `Age3AI.xs`:

    ```cpp title="foo.xs"
    void foo(void)
    {
        aiEcho("Hello from foo!");
    }
    ```

    We can include it like this:

    ```cpp title="Age3AI.xs"
    include "./foo.xs";

    void main(void)
    {
        foo();
    }
    ```

    Which will ultimately look like this once the game is done putting files
    together:

    ```cpp title="Age3AI.xs"
    void foo(void)
    {
        aiEcho("Hello from foo!");
    }

    void main(void)
    {
        foo();
    }
    ```

Absolute and relative paths are both supported.

Absolute paths start at the **AI Root Folder**.
