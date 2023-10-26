# Resource Gathering Systems

The following constants are used to identify Resource Gathering Systems.

```cpp title="Resource Gathering Systems"
// Script-based gatherer allocation. The entire calculation is
// written in the AI script.
extern const int cRGPScript = 0;

// Cost-based gatherer allocation. The formula is hidden in the
// game itself but can be influenced by assigning costs to each
// resource type.
extern const int cRGPCost = 1;

// Weighted average of the above.
extern const int cRGPActual = 2;
```
