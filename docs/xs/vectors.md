# Vectors

A vector is a data type that represents a point in space. It is made up of
three numbers, which represent the x, y, and z coordinates of the point:

- `x` goes from the bottom to the right corner of the map.
- `y` is the elevation.
- `z` goes from the bottom to the left corner of the map.

Vectors are usually used to represent a position on the map, but can also be
used to represent a direction, and can have other, less common uses.

## 1. Creating a vector

To create a vector, use the `xsVectorSet` function. It takes three
parameters: the x, y, and z coordinates of the vector.

!!! note "Signature of `xsVectorSet`"

    ```cpp
    vector xsVectorSet(float x = 0.0, float y = 0.0, float z = 0.0);
    ```

!!! example "Creating a vector"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector origin = xsVectorSet(0.0, 0.0, 0.0);
        aiEcho("The origin is at " + origin);
    }
    ```

## 2. Changing a specific component of a vector

To change a specific component of a vector, use `xsVectorSetX`, `xsVectorSetY`,
or `xsVectorSetZ`, depending on which component you want to change. They take
two parameters: the vector to change, and the new value of the component.

!!! note "Signatures of vector setters"

    ```cpp
    // Set the x component of the given vector, returns the new vector.
    vector xsVectorSetX(vector v = cOriginVector, float x = 0.0);

    // Set the y component of the given vector, returns the new vector.
    vector xsVectorSetY(vector v = cOriginVector, float y = 0.0);

    // Set the z component of the given vector, returns the new vector.
    vector xsVectorSetZ(vector v = cOriginVector, float z = 0.0);
    ```

!!! example "Changing a specific component of a vector"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector point = cOriginVector;
        aiEcho("The point is at " + point);

        point = xsVectorSetX(point, 10.0);
        aiEcho("The point is now at " + point);
    }
    ```

## 3. Getting a specific component of a vector

To get a specific component of a vector, use `xsVectorGetX`, `xsVectorGetY`,
or `xsVectorGetZ`, depending on which component you want to get. They take one
parameter: the vector to get the component from.

!!! note "Signatures of vector getters"

    ```cpp
    // Get the x component of the given vector.
    float xsVectorGetX(vector v = cOriginVector);

    // Get the y component of the given vector.
    float xsVectorGetY(vector v = cOriginVector);

    // Get the z component of the given vector.
    float xsVectorGetZ(vector v = cOriginVector);
    ```

!!! example "Getting a specific component of a vector"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector point = cOriginVector;
        aiEcho("The point is at " + point);

        float x = xsVectorGetX(point);
        aiEcho("The x component of the point is " + x);
    }
    ```

## 4. Vector operations

### 4.1. Addition

!!! example "Adding two vectors"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector a = xsVectorSet(1.0, 2.0, 3.0);
        vector b = xsVectorSet(4.0, 5.0, 6.0);
        vector c = a + b;

        aiEcho("a + b = " + c);
    }
    ```

### 4.2. Subtraction

!!! example "Subtracting two vectors"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector a = xsVectorSet(1.0, 2.0, 3.0);
        vector b = xsVectorSet(4.0, 5.0, 6.0);
        vector c = a - b;

        aiEcho("a - b = " + c);
    }
    ```

### 4.3. Scalar multiplication

!!! example "Multiplying a vector by a scalar"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector a = xsVectorSet(1.0, 2.0, 3.0);
        vector b = a * 2.0;

        aiEcho("a * 2 = " + b);
    }
    ```

!!! warning "The order matters"

    Multiplying a vector by a scalar is not the same as multiplying a scalar
    by a vector. The order matters!

    ```cpp title="This will cause an error"
    void main(void)
    {
        vector a = xsVectorSet(1.0, 2.0, 3.0);
        vector b = 2.0 * a;

        aiEcho("2 * a = " + b);
    }
    ```

### 4.4. Scalar division

!!! example "Dividing a vector by a scalar"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector a = xsVectorSet(1.0, 2.0, 3.0);
        vector b = a / 2.0;

        aiEcho("a / 2 = " + b);
    }
    ```

### 4.5. Length

!!! example "Getting the length of a vector"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector a = xsVectorSet(1.0, 2.0, 3.0);
        float length = xsVectorLength(a);

        aiEcho("The length of a is " + length);
    }
    ```

### 4.6. Normalization

!!! example "Normalizing a vector"

    ```cpp title="Age3AI.xs"
    void main(void)
    {
        vector a = xsVectorSet(1.0, 2.0, 3.0);
        vector b = xsVectorNormalize(a);

        aiEcho("The normalized vector is " + b);
    }
    ```
