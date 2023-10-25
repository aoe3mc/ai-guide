# Rules

Rules are blocks of code that are periodically executed at a certain interval.
All of the concrete things the AI does, such as scouting, gathering, attacking,
etc. happen in rules.

## 1. Definition

Defining a rule means creating a new rule by giving it a name and a body. Rules
must be defined before they can be used.

!!! note "Syntax of rule definition"

    ```text
    rule ruleName
    group groupName
    active/inactive
    minInterval intervalValue
    maxInterval intervalValue
    highFrequency
    runImmediately
    priority priorityValue
    {
        // body
    }
    ```

### 1.1. Rule name

Rule names follow the same rules as [variable names](variables.md#212-name).

- Names are case-sensitive, e.g. `foo` and `Foo` are two different names.
- Names can only contain letters, numbers and underscores. Diacritics are not
  allowed.
- Names must start with a letter or an underscore.
- Names cannot be the same as a [keyword](../reference/keywords.md).
- Rules cannot have the same name as a [variable](variables.md), constant,
  [function](functions.md), [rule group](rules.md#2-rule-groups) or another
  rule.

### 1.2. Group name

See [rule groups](rules.md#4-rule-groups).

This can be omitted if the rule is not part of a group.

### 1.3. Active/Inactive

This is the initial state of the rule.

- `active` means the rule is enabled by default, and will run as soon as its
  first interval is reached.
- `inactive` means the rule is disabled by default, and will not run until it
  is enabled.

If this omitted, the rule will be `active` by default.

### 1.4. Min/Max interval

These are the minimum and maximum intervals between two consecutive executions
of the rule. The interval is measured in seconds.

- `minInterval` is the minimum interval that must pass before the rule can be
  executed again.
- `maxInterval` is the maximum interval that can pass before the rule must be
  executed again.

!!! tip "`minInterval` is, by far, more frequently used than `maxInterval`"

`minInterval` and `maxInterval` cannot be used with `highFrequency`.

### 1.5. High frequency

When this keyword is present, the rule will be executed 60 times per physical
second, i.e. independent of the game speed.

`highFrequency` cannot be used with `minInterval` or `maxInterval`.

### 1.6. Run immediately

By default, when rules are enabled, they will wait for their first interval to
pass before running. This keyword can be used to make the rule run immediately
after it is enabled.

### 1.7. Priority

Rules are executed in order of priority. The higher the priority, the sooner the
rule will be executed.

This can be omitted to let the game decide the priority of the rule.

### 1.8. Body

This can be any valid code except for a function definition or another rule
definition.

### 1.9. Examples

!!! example "Example of a rule definition"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        aiEcho("It has begun!");
    }

    rule TimeElapsed
    active
    minInterval 5
    runImmediately
    {
        int timeElapsed = xsGetTime() / 1000;
        aiEcho("" + timeElapsed + " seconds have passed since the game started.");
    }
    ```

## 2. Enabling rules

Rules can be enabled with the `xsEnableRule` function.

!!! note "Signature of `xsEnableRule`"

    ```cpp
    // Enables the rule with the given name.
    void xsEnableRule(string ruleName = "");
    ```

!!! example "Using `xsEnableRule` to enable a rule"

    This is the same example as above, but now the rule is disabled by default
    and we enable it manually.

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        aiEcho("It has begun!");
        xsEnableRule("TimeElapsed");
    }

    rule TimeElapsed
    inactive
    minInterval 5
    runImmediately
    {
        int timeElapsed = xsGetTime() / 1000;
        aiEcho("" + timeElapsed + " seconds have passed since the game started.");
    }
    ```

## 3. Disabling rules

Rules can be disabled with the `xsDisableRule` function. Rules can also disable
themselves with the `xsDisableSelf` function.

!!! note "`xsDisableSelf` and `xsDisableRule` signatures"

    ```cpp
    // Disables the rule in which it is called.
    void xsDisableSelf(void);
    // Disables the rule with the given name.
    void xsDisableRule(string ruleName = "");
    ```

!!! example "Disabling a rule"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        aiEcho("It has begun!");
    }

    rule ManageCommunication
    active
    minInterval 1
    runImmediately
    {
        // Say hello in the beginning.
        if (xsGetTime() < 1000)
        {
            xsEnableRule("SayHello");
        }

        // Say goodbye after 10 seconds and disable this rule.
        if (xsGetTime() >= 10000)
        {
            xsEnableRule("SayGoodbye");
            xsDisableSelf();
        }
    }

    rule SayHello
    inactive
    runImmediately
    {
        aiEcho("Hello!");
        xsDisableSelf();
    }

    rule SayGoodbye
    inactive
    runImmediately
    {
        aiEcho("Goodbye!");
        xsDisableSelf();
    }
    ```

## 4. Rule groups

Rules can be grouped together. This is useful for enabling/disabling a group of
rules at once.

To create a group, use the `group` keyword in the rule definition, followed by
the name of the group. Group names follow the same rules as [variable
names](variables.md#212-name).

- Names are case-sensitive, e.g. `foo` and `Foo` are two different names.
- Names can only contain letters, numbers and underscores. Diacritics are not
  allowed.
- Names must start with a letter or an underscore.
- Names cannot be the same as a [keyword](../reference/keywords.md).
- Rule groups cannot have the same name as a [variable](variables.md), constant,
  [function](functions.md) or [rule](rules.md).

All rules that have the same group name will be part of the same group.

!!! example "Example of a rule group"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        aiEcho("It has begun!");
        xsEnableRuleGroup("rgCommunication");
    }

    // Say hello in the beginning.
    rule SayHello
    group rgCommunication
    inactive
    runImmediately
    {
        aiEcho("Hello!");
        xsDisableSelf();
    }

    // Say goodbye after 10 seconds.
    rule SayGoodbye
    group TimeElapsed
    inactive
    minInterval 10
    {
        aiEcho("Goodbye!");
        xsDisableSelf();
    }
    ```

## 5. Calling rules

Rules can be called like a function. This is useful when you want to execute a
rule immediately at a specific point in the code and without any interval.

For that, the rule needs to be define **before** it is called, i.e. written
anywhere above the call.

!!! example "Calling a rule"

    ```cpp title="Age3AI.xs"
    rule SayHello
    inactive
    {
        aiEcho("Hello!");
        xsDisableSelf();
    }

    void main(void)
    {
        aiEcho("It has begun!");
        SayHello();
    }
    ```
