# Assignment 9 - Core Gameplay Mechanic Prototype

## Mechanics & Purpose

We have implemented many of the core gameplay mechanics but the primary ones we will discuss are the reward system and the sprinting gauge. The purpose it to allow players a way to make their character more equipped to tackle the challenges up ahead.
## Blueprint
### Sprint / Stamina Gauge
The stamina mechanic is implemented with multiple functions. In order to explain it, we must break it down into it's functions within the EventGraph.
 
**Left Shift Key** - By adding the Left Shift key listener, we are able to know when the user has pressed the key and with that information we branch out to set our variable 'isRunning' to be true or false based off of if the key is pressed. This will then allow us to update the Max walk speed of our character and simultaneously call either the 'UseStamina' function to decrease the current stamina value or 'IncreaseStamina' to regenerate the value back to it's max.

**UseStamina** - A function that continues to reduce stamina until zero in which the character's movement will be reset to 500.

**IncreaseStamina** - A function to regenerate the stamina by 3 points up to the maximum stamina the player currently has. In order to have the upgraded stamina values remain across level change we put the variable in a game instance blueprint.

**Show Stamina Gauge with value** - In order to show the value to the viewport, we have to create a widget on BeginPlay and in that widget we must fetch the MaxStamina value in order for it to show on our User Interface.

### Rewards
Upgrades and rewards work the same way in our blueprints. When a player overlaps with the object, a sound is played and a text widget is added temporarily for feedback purposes and the object is destroyed.

## Behavior Tree
The behaviour tree has only been implemented with our enemy in the fog and chest monsters. The tree is implemented by having multiple sequences based off of the blackboard conditions that are set. In our case the variables we are using is ChasePlayer and PlayerCaught, in which if ChasePlayer is true then it will chase the player, if false then the idle animation will be played. Secondarily if Playercaught is true then the monster will play an attack animation and kill the player.

## Game Philosophy
 As Ninety-Nine floors is a game that is purely based off of dodging and overcoming obstacles, rather than fighting, it is important that the player has tools at their disposal to stay alive as they progress through the tower and challenge increasingly difficult stages.

## Challenge
The toughest challenge was having the values persist across all the levels because everytime we would change the level all the data would be reset. However, after some research, an instance could easily be implemented per game session so that the upgraded values would persist across teleportations.
