# kbGetPopCapAddition

## 1. Description

!!! note "Signature of `kbGetPopCapAddition`"

    ```cpp
    int kbGetPopCapAddition(int playerID, int protoUnitID);
    ```

This function returns how much population space the given proto unit provides
when it's on the map. If the proto unit doesn't provide any population space,
the function returns `#!cpp 0`.

## 2. Example

!!! example "Example using `kbGetPopCapAddition`"

    ```cpp title="Age3AI.xs" hl_lines="13 14"
    rule BuildHousesSpanish
    active
    minInterval 5
    {
        // Try to always have at least 10 population slots available.

        // Get the current population capacity.
        int currentPopCap = kbGetPopCap();

        // Get the current population count.
        int currentPopCount = kbGetPop();

        // Get the population space provided by a house.
        int popCapAddition = kbGetPopCapAddition(cMyID, cUnitTypeHouseMed);

        // Calculate how many houses we need to build to have 10 population
        // slots available.
        int housesToBuild = (currentPopCount + popCapAddition - currentPopCap) / popCapAddition;

        // Don't continue if we don't need to build any houses.
        if (housesToBuild <= 0)
        {
            return;
        }

        // Here the rest of the rule for building houses (irrelevant for this example)
    }
    ```
