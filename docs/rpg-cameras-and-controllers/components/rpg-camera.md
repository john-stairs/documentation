# RPG Camera

## Camera To Use

Use this variable to set up which camera game object should be used in the scene: 

- "Main Camera" will use the camera object which is tagged with "MainCamera"
- "Spawn Own Camera" will spawn a new camera object on start
- "Assigned Camera" will use the camera you assign to variable "Camera To Use"

## Used Skybox

Skybox which is currently used or should be used by the camera object. The skybox can be changed at runtime by calling the RPGCamera script's method `SetUsedSkybox(material)`. Direct assignments to this variable have no effect.

## Camera Pivot Local Position

This is the local position of the camera pivot, the "anchor" of the virtual camera. Turn on the script's Gizmos to visualize it as a small cyan sphere (see on the right).

<div style="text-align:center"><img src="../img/pivot-position.png"/></div>

## Internal and external Pivot

The RPGCamera also supports external pivots, i.e. pivots that are not within the character collider. When an external pivot is recognized, pivot occlusion and object fading between the character and the pivot is automatically turned on.

For internal pivots, there is additionally the possibility to enable the Intelligent Pivot that moves away from obstacles which the player could see through if zooming in enough, especially when using a wide screen.

## Always Activate Orbiting

If set to true, you do not have to press any input to control/rotate the camera.

## Align When Moving

If set to true, the camera view direction aligns with the character's view/walking direction when the character starts to move (forward/backwards/strafe). If additionally Support Walking Backwards is set to true, the camera faces the front of the character when walking backwards.

## Cursor Behavior Orbiting

Sets the cursor behavior during camera rotation/orbiting.

- "Move": The cursor continues to move as usual.
- "Move Confined": The cursor continues to move but is confined to the game window. According to Unity's documentation, only this mode is only "supported on the standalone player platform on Windows and Linux".
- "Stay": Before orbiting, the cursor position is memorized and restored after the orbiting ends. In combination with HideCursor = "When Orbiting", it looks like the cursor stayed where it was before starting the orbiting.
- "Lock in Center": The cursor jumps to the center of the screen and stays there as long as orbiting is active. Good for games where cursor controls are not foreseen, e.g. on consoles.

## Underwater Threshold Tuning

Gives the possibility to fine-tune the threshold where the camera is seen as underwater. The higher the value, the earlier the underwater effects kick in. The effects are enabled/disabled via methods `EnableUnderwaterEffects()` and `DisableUnderwaterEffects()`, respectively. You can override these two methods to implement your own visual effects.
