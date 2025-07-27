#Unity 
[[Gestalte]]

Flock simulator, space ship manager?

Game that is about moving making a captain of a fleet control the fleet from one location to another.
The game play elements are about placing predefined sensors to which the spaceships will react based on how far they are and changing the background prompt for the captain.

As level designer we can do stuff like place sensors ourselves, add obstacles like lava and walls.

To win, just like in Lemmings, you will need to let a percentage of the flock reach the end.

#### Lemmings
The Lemmings move around based on flock behavior, hopefully this will add more difficulty. In addition, the LLM can control the Lemmings based on the following exposed functions:
- **moveAwayFromSensor**: move all Lemmings in range away from the Sensor
- **moveCloserToSensor**: move all Lemmings in range closer to the Sensor
#### Sensors


#### Relevator
Distance



---
#### Environment controlled by a separate LLM?
**Not that fun**, feels like you have little control over the gaming element that is supposed to be controlled by the player.

---
#### Control ship in conjunction with LLM?
Maybe we can:
- Reduce speed
- Nudge ship in slight different direction
- Shoot stuff
The main direction and speed is controlled by the dumb LLM and we can do our best to help

TODO:
if not:
Make sensors detectable by ship
Make obstacles and see if we can make ship fly around it using sensors
