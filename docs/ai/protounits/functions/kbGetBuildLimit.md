# kbGetBuildLimit

## 1. Description

!!! note "Signature of `kbGetBuildLimit`"

    ```cpp
    int kbGetBuildLimit(int playerID, int protoUnitID);
    ```

This function returns the build limit of the given proto unit for the given
player. If the proto unit has no build limit, the function returns `#!cpp -1`.

## 2. Example

!!! example "Example using `kbGetBuildLimit`"

    ```cpp title="Age3AI.xs" hl_lines="5 6"
    rule BuildHousesSpanish
    active
    minInterval 5
    {
        // Get the build limit for houses.
        int buildLimit = kbGetBuildLimit(cMyID, cUnitTypeHouseMed);

        // Get the current number of houses (including those in progress).
        int currentCount = kbUnitCount(cMyID, cUnitTypeHouseMed, cUnitStateABQ);

        // If we have reached the build limit for houses, stop building them.
        if (currentCount >= buildLimit)
        {
            return;
        }

        // Here the rest of the rule for building houses (irrelevant for this example)
    }
    ```
