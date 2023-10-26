# Events

```cpp title="Events"
// When the AI's age changes.
extern const int cXSAgeHandler = 0;

// Untested.
extern const int cXSPowerHandler = 1;

// Untested.
extern const int cXSRetreatHandler = 2;

// When the opponent responds to the AI's resign request.
extern const int cXSResignHandler = 3;

// When a building is built.
extern const int cXSBuildHandler = 4;

// When a homecity shipment arrives (i.e. the card is activated).
extern const int cXSHomeCityTransportArriveHandler = 5;

// When a homecity shipment returns (i.e. the card could not be activated).
extern const int cXSHomeCityTransportReturnHandler = 6;

// When the homecity levels up.
extern const int cXSHomeCityLevelUpHandler = 7;

// When the treaty time is up.
extern const int cXSTreatyBrokenHandler = 8;

// When the AI gains a homecity shipment point.
extern const int cXSShipResourceGranted = 9;

// When a plan is generated (i.e. not created by aiPlanCreate)
extern const int cXSAutoCreatePlanHandler = 10;

// When someone claims a treasure.
extern const int cXSNuggetHandler = 11;

// When someone's age changes.
extern const int cXSPlayerAgeHandler = 12;

// When an opportunity appears and needs to be scored.
extern const int cXSScoreOppHandler = 13;

// When a mission starts (related to goals and opportunities).
extern const int cXSMissionStartHandler = 14;

// When a mission ends (related to goals and opportunities).
extern const int cXSMissionEndHandler = 15;

// When the game is over.
extern const int cXSGameOverHandler = 16;

// When the monopoly timer starts.
extern const int cXSMonopolyStartHandler = 17;

// When the monopoly timer is broken.
extern const int cXSMonopolyEndHandler = 18;

// Untested.
extern const int cXSWonderVictoryStartHandler = 19;

// Untested.
extern const int cXSWonderVictoryEndHandler = 20;

// Untested.
extern const int cXSRelicVictoryStartHandler = 21;

// Untested.
extern const int cXSRelicVictoryEndHandler = 22;

// When the King Of The Hill timer starts.
extern const int cXSKOTHVictoryStartHandler = 23;

// When the King Of The Hill timer is broken.
extern const int cXSKOTHVictoryEndHandler = 24;

// When a plan is generated (i.e. not created by aiPlanCreate).
extern const int cXSAutoCreateBuildPlanHandler_DEPRECATED = 25;

// Untested.
extern const int cXSRevoltedHandler = 26;

// Untested.
extern const int cXSBuildingPlacementFailedHandler = 27;
```
