# Comments

Comments are a part of a script that the game ignores. Comments are used
to add short notes, reminders or a detailed documentation in a script. They can
also be used to temporarily disable certain parts of the code.

There are two types of comments:

- Inline comments.
- Block comments.

## 1. Inline comments

Inline comments begin with two forward slashes `//` and span a single line.

!!! example "Some examples of inline comments"

    ```cpp title="constants.xs"
    // This is the number PI.
    const float PI = 3.141592;
    // Degrees to radians conversion factor.
    const float cDegToRad = PI / 180.0;
    // Radians to degrees conversion factor.
    const float cRadToDeg = 180.0 / PI;
    ```

## 2. Block comments

Block comments begin with a forward slash followed by an asterisk `/*`, and end
with an asterisk followed by a forward slash `*/`. They can span multiple lines.

!!! example "Some examples of block comments"

    ```cpp title="main.xs"
    /*
      This is the "main" function of the script, also known as the "entry point".
      It is called when the map is fully loaded and before the first frame is
      rendered. Certain things, mostly initialization, should be done here.
    */
    void main(void)
    {
      /*
        Tell the system to divide the map into areas and area groups.
        This must be done, only once, and as early as possible.
      */
      kbAreaCalculate();

      /*
        Set the seed for the random number generator. -1 means a random seed.
        Use a specific seed to reproduce the same sequence of random numbers,
        which is useful for debugging.
      */
      aiRandSetSeed(-1);
    }
    ```

!!! danger "Do not nest block comments"

    Block comments cannot be nested.

    ```cpp
    /*
      If you look closely at the colors, you will notice
      /*
        that this comment is grey-colored because
        it is still inside the block comment.
      */
      Here, however, the comment is no longer grey-colored
      because it is outside the block comment. Avoid nesting
      block comments!
    */
    ```
