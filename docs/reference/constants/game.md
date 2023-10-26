# Game Constants

The following constants have different values depending on the configuration of
the current game.

```cpp title="Game Constants"
// Contains the current number of players, including Mother Nature.
extern const int cNumberPlayers;

// Contains the current game type(1)
extern const int cGameTypeCurrent;

// Contains the current game mode(2)
extern const int cGameModeCurrent;

// Contains the current difficulty(3)
extern const int cDifficultyCurrent;

// Contains the name of the random map the AI is currently
// playing on. If the AI is playing on a scenario, the value
// of this constant is "None".
extern const string cRandomMapName;
```

1.  See [Game Types](game-types.md) for possible values.
2.  See [Game Modes](game-modes.md) for possible values.
3.  See [Difficulties](difficulties.md) for possible values.
