# Player Relation Constants

The following constants are used to identify player relations.

```cpp title="Player Relation Constants"
// Any player.
extern const int cPlayerRelationAny = 99999;

// Context player.
extern const int cPlayerRelationSelf = 100000;

// Enemies, including Mother Nature.
extern const int cPlayerRelationEnemy = 100002;

// Allies, including self.
extern const int cPlayerRelationAlly = 100001;

// Enemies, excluding Mother Nature.
extern const int cPlayerRelationEnemyNotGaia = 100004;

// Allies, excluding self.
extern const int cPlayerRelationAllyExcludingSelf = 100005;
```
