# Labels

Labels are used to jump to a specific point in the script. They are defined by
the `label` keyword followed by the label name and a semicolon. Labels can be
used with the `goto` keyword to jump to the label.

Label names follow the same rules as [variable names](variables.md#212-name):

- Names are case-sensitive, e.g. `foo` and `Foo` are two different names.
- Names can only contain letters, numbers and underscores. Diacritics are not
  allowed.
- Names must start with a letter or an underscore.
- Names cannot be the same as a [keyword](../reference/keywords.md).
- Labels cannot have the same name as a [variable](variables.md), constant,
  [function](functions.md), [rule](rules.md) or [rule group](rules.md#12-group-name).

!!! note "Syntax of labels"

    ```text
    // Creating a label.
    label labelName;

    // Jumping to a label.
    goto labelName;
    ```

!!! example "Example of a label"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        aiEcho("Hello from above the label!");
        goto _SayGoodbye;
        aiEcho("Hello from a part of the code that won't be reached!");
        label _SayGoodbye;
        aiEcho("Hello from below the label! Goodbye!");
    }
    ```

    ```text title="AI Debug Output"
    00:00:00 (0): P#1 (Player 1) Hello from above the label!
    00:00:00 (0): P#1 (Player 1) Hello from below the label! Goodbye!
    ```

!!! tip "Naming convention for labels"

    Since labels are rarely used, there's no naming convention for them. You can
    use whatever style you want but it's important to be consistent.

    In this guide, we will prefix labels with an underscore (`_`).

!!! warning "Duplicate labels"

    The game does not prevent you from creating multiple labels with the same
    name. It's not fully clear what happens when you do this, but it's best to
    avoid it.
