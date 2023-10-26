# Default Escrows

The following constants are used to identify built-in escrows.

```cpp title="Default Escrows"
// Default resource inventory.
// Resources are moved here for certain operations.
extern const int cRootEscrowID = 0;

// Resource inventory for economy plans.
extern const int cEconomyEscrowID = 1;

// Resource inventory for military plans.
extern const int cMilitaryEscrowID = 2;

// "Emergency" can be used to "steal" resources from
// other escrows (in theory).
extern const int cEmergencyEscrowID = -2;
```
