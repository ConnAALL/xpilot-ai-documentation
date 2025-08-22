# XPilot-AI Function Library

## Overview

> **Coordinate System:** In Xpilot-AI, **0 degrees is to the right** and **90 degrees is up**.

> **Important:** Many of the item related functions simulate keypresses. So, for example, if pressing `Tab` would not place a mine (say, because you have none), `dropMine()` will not either.

**ID functions** refer to a specific ship's ID, while **IDX functions** refer to the ship's index within your buffer.

## Initialization Functions

### Basic Setup
```c
void headlessMode()
```
Execute this before start to run windowless.

### Language-Specific Initialization

**C:**
```c
int start(int argc, char* argv[])
```
Initializes the AI interface and starts Xpilot

**Java:**
```java
Class var = new Class(String[] args);
```
Initializes the AI interface and starts Xpilot

**Python:**
```python
start(func, ["listof","args"])
```
Initializes the AI interface and starts Xpilot

**Racket:**
```racket
(start func '("listof" "args"))
```
Initializes the AI interface and starts Xpilot

---

## Capture the Flag Functions

```c
int ballX()
```
Returns the x position of the first ball found on the map. Returns `-1` if no balls are found.

```c
int ballY()
```
Returns the y position of the first ball found on the map. Returns `-1` if no balls are found.

```c
int connectorX0()
```
Returns the X position of the point that is one end of the connector. Returns `-1` if no connectors are found.

```c
int connectorX1()
```
Returns the X position of the point that is the other end of the connector. Returns `-1` if no connectors are found.

```c
int connectorY0()
```
Returns the Y position of the point that is one end of the connector. Returns `-1` if no connectors are found.

```c
int connectorY1()
```
Returns the Y position of the point that is the other end of the connector. Returns `-1` if no connectors are found.

---

## Closest Functions

```c
int closestRadarX()
```
Returns the closest ship's X radar coordinate `(0-256)`. Returns `-1` if there are no ships on the radar.

```c
int closestRadarY()
```
Returns the closest ship's Y radar coordinate `(0-256)`. Returns `-1` if there are no ships on the radar.

```c
int closestItemX()
```
Returns the closest item's X radar coordinate. Returns `-1` if there are no items on the screen.

```c
int closestItemY()
```
Returns the closest item's Y radar coordinate. Returns `-1` if there are no items on the screen.

```c
int closestShipId()
```
Returns the closest ship's ID. Returns `-1` if there are no ships on the screen.

---

## ID Functions

> Functions that work with specific ship IDs

```c
double enemySpeedId(int id)
```
Returns the speed of the specified enemy in pixels per frame. Returns `-1` if the specified id could not be found.

```c
double enemyTrackingRadId(int id)
```
Returns the direction in which the specified enemy is moving in radians. Returns `0.0` if the specified id could not be found.

```c
double enemyTrackingDegId(int id)
```
Returns the direction in which the specified enemy is moving in degrees. Returns `0.0` if the specified id could not be found.

```c
int enemyReloadId(int id)
```
Returns the specified enemy's reload time remaining. Returns `-1` if the specified id could not be found.

```c
int screenEnemyXId(int id)
```
Returns the specified enemy's X coordinate on the map. Returns `-1` if the specified id could not be found.

```c
int screenEnemyYId(int id)
```
Returns the specified enemy's Y coordinate on the map. Returns `-1` if the specified id could not be found.

```c
double enemyHeadingDegId(int id)
```
Returns the direction the specified enemy is facing in degrees. Returns `-1` if the specified id could not be found.

```c
double enemyHeadingRadId(int id)
```
Returns the direction the specified enemy is facing in radians. Returns `-1` if the specified id could not be found.

```c
int enemyShieldId(int id)
```
Returns `1` if the specified enemies shield is up, `0` if it is down, or `-1` if the specified id could not be found.

```c
int enemyLivesId(int id)
```
Returns the specified enemy's remaining lives (if there is a limit) or the number of lives spent. Returns `-1` if the specified id could not be found.

```c
char* enemyNameId(int id)
```
Returns the specified enemy's name. Returns `NULL` if the specified id could not be found.

```c
double enemyScoreId(int id)
```
Returns the specified enemy's score. Returns `-1` if the specified id could not be found.

```c
int enemyTeamId(int id)
```
Returns the specified enemy's team ID. Returns `-1` if the specified id could not be found. Returns `-1` if there are no teams.

```c
double enemyDistanceId(int id)
```
Returns the distance between the ship and the specified enemy. Returns `-1` if the specified id could not be found.

---

## IDX Functions

> **Ships are sorted from near (nearest at index 0) to far. Only ships that are on screen should be accessible.**

```c
double enemyDistance(int idx)
```
Returns the distance between the ship and the specified enemy.

```c
double enemySpeed(int idx)
```
Returns the speed of the specified enemy.

```c
int enemyReload(int idx)
```
Returns the specified enemy's reload time remaining.

```c
double enemyTrackingRad(int idx)
```
Returns the specified enemy's tracking in radians.

```c
double enemyTrackingDeg(int idx)
```
Returns the specified enemy's tracking in degrees.

```c
int screenEnemyX(int idx)
```
Returns the specified enemy's X coordinate on the map.

```c
int screenEnemyY(int idx)
```
Returns the specified enemy's Y coordinate on the map.

```c
double enemyHeadingDeg(int idx)
```
Returns the direction the specified enemy is facing in degrees.

```c
double enemyHeadingRad(int idx)
```
Returns the direction the specified enemy is facing in radians.

```c
int enemyShield(int idx)
```
Returns the specified enemy's shield status.

```c
int enemyLives(int idx)
```
Returns the specified enemy's remaining lives. Returns `-1` if the corresponding object cannot be found within the Others array.

```c
int enemyTeam(int idx)
```
Returns the specified enemy's team. Returns `-1` if the corresponding object cannot be found within the Others array.

```c
char* enemyName(int idx)
```
Returns the specified enemy's name. Returns empty string if the corresponding object cannot be found within the Others array.

```c
double enemyScore(int idx)
```
Returns the specified enemy's score. Returns `0.0` if the corresponding object cannot be found within the Others array.

---

## Item Usage Methods

```c
void tankDetach()
```
Detaches a fuel tank from the ship.

```c
void cloak()
```
Cloaks the ship from sight.

```c
void ecm()
```
Launches an ECM to temporarily blind opponents.

```c
void transporter()
```
Uses the transporter item to steal an opponent's item or fuel supply.

```c
void tractorBeam(int flag)
```
Uses the ship's tractor beam to pull in enemy ships. Flag is either `1`, to virtually hold down the key, or `0`, to release the key.

```c
void pressorBeam(int flag)
```
Uses the ship's pressor beam to push away enemy ships. Flag is either `1`, to virtually hold down the key, or `0`, to release the key.

```c
void phasing()
```
Uses the phasing item to allow the ship to pass through walls.

```c
void shield(int flag)
```
Turns on or off the ship's Shield. Flag is either `1`, to virtually hold down the key (shields up), or `0`, to release the key (shields down).

```c
void emergencyShield()
```
Uses the emergency shield item to protect your ship from damage for a period of time.

```c
void hyperjump()
```
Uses the hyper jump item to warp the ship to a random location on the map.

```c
void nextTank()
```
Switches to the ship's next fuel tank.

```c
void prevTank()
```
Switches to the ship's previous fuel tank.

```c
void toggleAutopilot()
```
Uses the autopilot item to stop the ship's movement.

```c
void emergencyThrust()
```
Uses the emergency thrust item to increase the ship's movement speed for a period of time.

```c
void deflector()
```
Uses the deflector item to push everything away from the ship.

```c
void selectItem()
```
Selects the ship's item to be dropped.

```c
void loseItem()
```
Drops the ship's selected item.

---

## Lock Methods

```c
void lockNext()
```
Locks onto the next ship in the ship buffer.

```c
void lockPrev()
```
Locks onto the prev ship in the ship buffer.

```c
void lockClose()
```
Locks onto the closest ship.

```c
void lockNextClose()
```
Locks-on to the next closest ship.

```c
void loadLock1()
```
Load a saved lock-on enemy ship

```c
void loadLock2()
```
Load a saved lock-on enemy ship

```c
void loadLock3()
```
Load a saved lock-on enemy ship

```c
void loadLock4()
```
Load a saved lock-on enemy ship

---

## Map Features

```c
void connector(int flag)
```
Connects the ship to the ball in Capture the Flag Mode. Flag is either `1`, to virtually hold down the key, or `0`, to release the key.

```c
void dropBall()
```
Drops the ball in Capture the Flag Mode.

```c
void refuel(int flag)
```
Refuels the ship. Flag is either `1`, to virtually hold down the key, or `0`, to release the key.

---

## Modifier Methods

```c
void toggleNuclear()
```
Toggles the option to have the ship fire **Nuclear weapons** instead of regular weapons, takes up five mines or seven missiles per shot.

```c
void togglePower()
```
Toggles the power levels of the ship's weapons.

```c
void toggleVelocity()
```
Modifies the explosion velocity of mines and missiles.

```c
void toggleCluster()
```
Toggles the option to have the ship fire **Cluster weapons** instead of regular weapons.

```c
void toggleMini()
```
Toggles the option to have the ship fire **Mini weapons** instead of regular weapons.

```c
void toggleSpread()
```
Toggles the option to have the ship fire **Spread weapons** instead of regular weapons.

```c
void toggleLaser()
```
Toggles between the **LS stun laser** and the **LB blinding laser**.

```c
void toggleImplosion()
```
Toggle the option to have mines and missiles **implode** instead of explode, the explosion will draw in players instead of blowing them away.

```c
void toggleUserName()
```
Toggles the displayed information on the HUD on the left of the screen.

```c
void loadModifiers1()
```
Loads Modifiers.

```c
void loadModifiers2()
```
Loads Modifiers.

```c
void loadModifiers3()
```
Loads Modifiers.

```c
void loadModifiers4()
```
Loads Modifiers.

```c
void clearModifiers()
```
Clears Modifiers.

---

## Movement Methods

```c
void turnLeft(int flag)
```
Turns the ship left. Flag is either `1`, to virtually hold down the key, or `0`, to release the key.

```c
void turnRight(int flag)
```
Turns the ship right. Flag is either `1`, to virtually hold down the key, or `0`, to release the key.

```c
void turn(int deg)
```
Turns the ship in the specified number of degrees.

```c
void turnToDeg(int deg)
```
Turns the ship towards the specified heading in degrees.

```c
void thrust(int flag)
```
Turns the ship's thrusters on or off. Flag is either `1`, to virtually hold down the key, or `0`, to release the key.

```c
void setTurnSpeed(double s)
```
Sets the speed the ship will turn by. The minimum power level is `4.0` and the maximum power level is `64.0`.

```c
void setTurnSpeedDeg(int s)
```
Ship turns to input degree.

```c
void setPower(double s)
```
Sets the amount of power the ship will use for thrusting, the minimum power level is `5.0` and the maximum power is `55.0`.

```c
void fasterTurnrate()
```
Increases the ship's turn rate.

```c
void slowerTurnrate()
```
Decreases the ship's turn rate.

```c
void morePower()
```
Increases the ship's thrusting power.

```c
void lessPower()
```
Decreases the ship's thrusting power.

---

## Other Options

```c
void keyHome()
```
Changes the ship's home base or respawn location.

```c
void selfDestruct()
```
Triggers the ship's self destruct mechanism.

```c
void pauseAI()
```
Pauses the game for the ship, does not affect other ships.

```c
void swapSettings()
```
Swaps between the ship's settings for turn rate and thrusting power.

```c
void quitAI()
```
Quits Xpilot.

```c
void talkKey()
```
Opens up the chat window.

```c
void toggleCompass()
```
Toggles the ship's Compass.

```c
void toggleShowMessage()
```
Toggles messages on the HUD on the left side of the screen.

```c
void toggleShowItems()
```
Toggles items on the HUD on the left side of the screen.

```c
void repair()
```
Repairs a target.

```c
void reprogram()
```
Reprograms a modifier or lock bank.

```c
void talk(char* talk_str)
```
Sends a message.

```c
char* scanMsg(int id)
```
Returns the specified player message. ID `0` is the most recent occurring message. If the id is past the max numbers of messages it returns empty string.

```c
char* scanGameMsg(int id)
```
Returns the specified game message. ID `0` is the most recent occurring message. If the id is past the max numbers of messages it returns empty string.

### Utility Functions

```c
double degToRad(int deg)
```
Converts degrees to radians.

```c
double radToDeg(double rad)
```
Converts radians to degrees.

```c
double angleDiff(int angle1, int angle2)
```
Calculates the difference between two angles. Output range `[-180,180]` degrees. Returns the smallest angle which angle1 could add to itself to be equal to angle2.

```c
double angleAdd(int angle1, int angle2)
```
Calculates the sum of two angles. Takes and returns in degrees. Output range `[0,360)`.

---

## Self Properties

```c
int selfX()
```
Returns the ship's X position on the map.

```c
int selfY()
```
Returns the ship's Y position on the map.

```c
int selfRadarX()
```
Returns the ship's X radar coordinate. If the ship is hidden from the radar returns `-1`.

```c
int selfRadarY()
```
Returns the ship's Y radar coordinate. If the ship is hidden from the radar returns `-1`.

```c
int selfVelX()
```
Returns the ship's X velocity.

```c
int selfVelY()
```
Returns the ship's Y velocity.

```c
int selfSpeed()
```
Returns the ship's speed.

```c
double lockHeadingDeg()
```
Returns in degrees the direction of the ship's lock-on of an enemy. (Direction from ship to target ship)

```c
double lockHeadingRad()
```
Returns in radians the direction of the ship's lock-on of an enemy. (Direction from ship to target ship)

```c
short selfLockDist()
```
Returns the distance of the enemy that the ship has locked-on to. Need to check this.

```c
int selfReload()
```
Returns the player's reload time remaining, based on a call to `fireShot()`. `0` means that the ship is able to fire again.

```c
int selfID()
```
Returns the ID of the ship.

```c
int selfAlive()
```
Returns `0` if the ship is dead or `1` if alive.

```c
int selfTeam()
```
Returns an integer corresponding to the ship's team.

```c
int selfLives()
```
Returns how many lives are left for the ship (if there is a life limit). Otherwise it returns the number of lives spent.

```c
double selfTrackingRad()
```
Returns the ship's tracking (direction it is moving in) in radians. If the ship is not moving it returns the direction the ship is facing.

```c
double selfTrackingDeg()
```
Returns the ship's tracking (direction it is moving in) in degrees. If the ship is not moving it returns the direction the ship is facing.

```c
double selfHeadingDeg()
```
Returns the direction the ship is facing in degrees.

```c
double selfHeadingRad()
```
Returns the direction the ship is facing in radians.

### HUD Functions

```c
char* hud(int i)
```
Returns the name of the object with index i in the score_objects list.

```c
char* hudScore(int i)
```
Returns the score of object at index i of score_objects on the HUD.

```c
double hudTimeLeft(int i)
```
Returns the remaining time left on the HUD for a score of object at index i of score_objects in seconds.

```c
double getTurnSpeed()
```
Returns the ship's turn speed.

```c
double getPower()
```
Returns the ship's power level.

```c
int selfShield()
```
Returns `1` if the player's shield is on, `0` if it's down, or `-1` if the player is not alive.

```c
char* selfName()
```
Returns the ship's name.

```c
double selfScore()
```
Returns the ship's score.

### Wall Detection

```c
int wallFeeler(int dist, int angle)
```
Takes a distance to search from the ship (`dist`), and an angle to search in degrees (`angle`). If no wall is felt it returns `dist`. If a wall is felt it returns the wall's distance from the ship.

```c
int wallFeelerRad(int dist, double a)
```
Takes a distance to search from the ship (`dist`), and an angle to search in radians (`a`). If no wall is felt it returns `dist`. If a wall is felt it returns the wall's distance from the ship.

```c
int wallBetween(int x1, int y1, int x2, int y2)
```
If there is a wall between the given points it returns the distance from point 1 to the first found wall. If no wall is found it returns `-1`.

---

## Shooting Methods

```c
void fireShot()
```
Fires a shot from the ship's main cannon.

```c
void fireMissile()
```
Fires a missile from the ship.

```c
void fireTorpedo()
```
Fires a torpedo from the ship.

```c
void fireHeat()
```
Fires a heat seeking missile from the ship.

```c
void dropMine()
```
Drops a stationary mine from the ship.

```c
void detachMine()
```
Releases a mine from the ship that will have the same velocity as the ship upon point of detachment.

```c
void detonateMines()
```
Detonates mines previously released from the ship.

```c
void fireLaser()
```
Fires a laser from the ship.

---

## Shot Functions

> **These will return `-1` if the buffer has no shot at the given index. Buffer is sorted near (nearest at 0) to far. Shots that are not on the screen should not be in the buffer.**

```c
int shotAlert(int idx)
```
Returns a danger rating of a shot, the smaller the number the more likely the shot is to hit the ship.

```c
int shotX(int idx)
```
Returns the X coordinate of a shot on the map.

```c
int shotY(int idx)
```
Returns the Y coordinate of a shot on the map.

```c
int shotDist(int idx)
```
Returns the distance of a shot from the ship.

```c
int shotVel(int idx)
```
Returns the velocity of a shot. (Technically speed, velocity is a vector, not a scalar)

```c
int shotVelDir(int idx)
```
Returns the direction of the velocity of a shot. (in degrees)

```c
int aimdir(int idx)
```
Returns the direction that the ship needs to turn to in order to face the enemy in degrees. Fails and returns `-1` under a few conditions.
