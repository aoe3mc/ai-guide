# Arrays

Arrays allow you to store multiple values in a single variable. They are
useful for storing lists of things, e.g. a list of units you want the AI to
train.

## 1. Creating an array

To create an array, you need to use one of the following functions (depending
on the data type you want to store):

!!! note "Signatures of `xsArrayCreate` functions"

    ```cpp
    // Creates a sized and named boolean array, returning an arrayID.
    int xsArrayCreateBool(int size = -1, bool defaultValue = false, string name = "");

    // Creates a sized and named integer array, returning an arrayID.
    int xsArrayCreateInt(int size = -1, int defaultValue = 0, string name = "");

    // Creates a sized and named float array, returning an arrayID.
    int xsArrayCreateFloat(int size = -1, float defaultValue = 0.0, string name = "");

    // Creates a sized and named string array, returning an arrayID.
    int xsArrayCreateString(int size = -1, string defaultValue = "", string name = "");

    // Creates a sized and named vector array, returning an arrayID.
    int xsArrayCreateVector(int size = -1, vector defaultValue = cInvalidVector, string name = "");
    ```

### 1.1. Array size

The `size` parameter specifies how many elements the array should have. It is
not possible to add more elements to an array than its size. If you want to
add more elements to an array, you need to use the `xsArrayResize` functions.

### 1.2. Array name

This is used for debugging purposes, and must be unique. It can be a concise
name or a slightly longer description of what the array is used for.

### 1.3. Array default value

This is the value that will be assigned to each element of the array when it
is created. Until you assign a different value to an element, it will have
this value.

## 2. Accessing array elements

To access an element of an array, you need to use one of the following
functions (depending on the data type the array stores):

!!! note "Signatures of `xsArrayGet` functions"

    ```cpp
    // Returns the value at the specified index in the requested array.
    bool xsArrayGetBool(int arrayID = -1, int index = -1);
    int xsArrayGetInt(int arrayID = -1, int index = -1);
    float xsArrayGetFloat(int arrayID = -1, int index = -1);
    string xsArrayGetString(int arrayID = -1, int index = -1);
    vector xsArrayGetVector(int arrayID = -1, int index = -1);
    ```

### 2.1. Array ID

This is the ID of the array you want to access. It is returned by the
`xsArrayCreate` functions.

### 2.2. Array index

This is the index of the element you want to access. The first element of an
array has index 0, the second element has index 1, and so on. If the index is
out of bounds (i.e. less than 0 or greater than or equal to the array size),
the function will return the default value of the array.

## 3. Assigning values to array elements

To assign a value to an element of an array, you need to use one of the
following functions (depending on the data type the array stores):

!!! note "Signatures of `xsArraySet` functions"

    ```cpp
    // Sets the value at the specified index in the requested array.
    void xsArraySetBool(int arrayID = -1, int index = -1, bool value = false);
    void xsArraySetInt(int arrayID = -1, int index = -1, int value = -1);
    void xsArraySetFloat(int arrayID = -1, int index = -1, float value = -1.0);
    void xsArraySetString(int arrayID = -1, int index = -1, string value = "");
    void xsArraySetVector(int arrayID = -1, int index = -1, vector value = cInvalidVector);
    ```

### 3.1. Array ID

This is the ID of the array you want to access. It is returned by the
`xsArrayCreate` functions.

### 3.2. Array index

This is the index of the element you want to access. The first element of an
array has index 0, the second element has index 1, and so on. If the index is
out of bounds (i.e. less than 0 or greater than or equal to the array size),
the function will do nothing.

### 3.3. Value

This is the value you want to assign to the element. It must be of the same
data type as the array.

## 4. Resizing arrays

To resize an array, you need to use one of the following functions (depending
on the data type the array stores):

!!! note "Signatures of `xsArrayResize` functions"

    ```cpp
    // Resize the requested array.
    bool xsArrayResizeBool(int arrayID = -1, int newSize = -1);
    bool xsArrayResizeInt(int arrayID = -1, int newSize = -1);
    bool xsArrayResizeFloat(int arrayID = -1, int newSize = -1);
    bool xsArrayResizeString(int arrayID = -1, int newSize = -1);
    bool xsArrayResizeVector(int arrayID = -1, int newSize = -1);
    ```

### 4.1. Array ID

This is the ID of the array you want to resize. It is returned by the
`xsArrayCreate` functions.

### 4.2. New size

This is the new size of the array. If it's less than the current size, the
array will be truncated. If it's greater than the current size, the array will
be extended, and the new elements will be initialized to the default value of
the array. If it's negative, the function will do nothing and the array will
remain unchanged.

## 5. Examples

!!! example "Example of array usage"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        int lowTierInfantry = xsArrayCreateInt(2, -1, "List of low-tier infantry units");
        xsArraySetInt(lowTierInfantry, 0, cUnitTypePikeman);
        xsArraySetInt(lowTierInfantry, 1, cUnitTypeCrossbowman);

        int highTierInfantry = xsArrayCreateInt(2, -1, "List of high-tier infantry units");
        xsArraySetInt(highTierInfantry, 0, cUnitTypeHalberdier);
        xsArraySetInt(highTierInfantry, 1, cUnitTypeSkirmisher);

        for (int i = 0; i < xsArrayGetSize(lowTierInfantry); i++)
        {
            int unitType = xsArrayGetInt(lowTierInfantry, i);
            string unitName = kbGetUnitTypeName(unitType);
            aiEcho("Low-tier infantry unit at index " + i + ": " + unitName);
        }

        for (int i = 0; i < xsArrayGetSize(highTierInfantry); i++)
        {
            int unitType = xsArrayGetInt(highTierInfantry, i);
            string unitName = kbGetUnitTypeName(unitType);
            aiEcho("High-tier infantry unit at index " + i + ": " + unitName);
        }
    }
    ```
