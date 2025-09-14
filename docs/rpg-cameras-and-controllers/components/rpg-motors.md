# RPG Motors

## Camera-Controlled 3D Movement (MMO only)

If set to true, character 3D movement, e.g. diving or surfacing, is only possible when the character should align/rotate with the camera. Otherwise, the character will always move into viewing direction irrespective of alignment input.

## Align With Camera

Determines when the character’s view/walking direction should be aligned to the camera’s view direction.

## Allowed Airborne Moves

The character is allowed to move slightly while airborne after performing a standing jump. This variable saves the maximum number of allowed airborne moves.

## Allowed Midair Jumps

Only visible when EnableMidairJumps is set to true. Determines the number of additional jumps while in midair.

## Climbing configuration

In the RPGMotor, two different types of climbing are distinguished: Ledge Grabbing and Free Climbing. Both functionalities can be independently turned on and off. Ledge Grabbing enables the character to hold on ledges, move along them and climb them up if possible. Free Climbing basically covers the rest: climbing freely in all directions along a wall or generally any collider, without the possibility to automatically grab or climb up ledges.

For setting up one or both of them, I recommend turning on variable "Draw Check Gizmos". As a result, gizmos are drawn that show which areas are checked for the hands and feet, i.e. their position (hands/feet height), the grab range between them, hands/feet size (check radius) and grab distance (how far away a ledge can be to grab it). Additionally, there are variables for setting the maximum angle a ledge or a collider can have to be considered climbable, and for specifying a cooldown after climbing was finished/canceled. Also do not forget to set assign climbable objects to a certain layer which is also part of the "Climbable Layers" layer mask in the inspector.

## Falling Threshold

A value representing the degree at which the character starts to fall. The default value is "6" to let the character be grounded when walking down small hills.

## Grounded Tolerance

Tolerance height used for the grounded check. The larger the value, the larger the distance to the ground which enables grounded character behavior to true. Useful for tweaking character movement on debris.

## Sliding Timeout

Generally, sliding occurs whenever the terrain/ground is steeper than the "Slope Limit" given in the Character Controller component. This variable gives the time in seconds which has to pass before the sliding logic kicks in.

## Swimming Start Height

Defines the local water height at which the character should start to swim. Enable Gizmos for easier setup.
