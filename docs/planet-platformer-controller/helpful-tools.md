# Helpful tools

In the following, tools for easier scene setup and maintenance will be explained.

## Gizmos and debugging rays

Almost every script implements multiple gizmos to make the setup of public variables easier. In the following, the most important ones are described.

### Scene view

Gizmos related to the character:

- Red (PPMotor): Ray for the grounded check. Its length can be adjusted via public variable "Grounded Tolerance". Turns green during play mode if the object is grounded.
- Black (PPMotor): Check rays for detecting ledges to hold on and climb up.
- Yellow (PPCharacter): Visualization of the punch height, radius and distance

<div style="text-align:center"><img src="../img/gizmos.png"/><br></div>

Gizmos related to vector/gravitational fields:

- Check "Draw Field" to draw the whole field in the given color. 
- Check "Draw Field Lines" to draw the given number of field lines in the given color. Field lines represent the "flow" of gravity inside the field

The different types of camera settings also have their own gizmos that are usually drawn at the scene's origin/center as anchor.

### Play mode

You can check public variable "Enable Debugging Rays" of the PPMotor to draw additional debugging rays during play mode:

- Magenta: Internally calculated movement direction
- Gray: Applied gravity vector
- Black: Velocity of the rigidbody
- Green: Internally calculated "forward" movement direction of the character (up/down input is mapped to this vector)
- Yellow: Internally calculated "right" movement direction of the character (left/right input is mapped to this vector)

Besides that, there is also the possibility to highlight the strongest gravitational field, i.e. the field that currently affects the character, via checking PPMotor parameter "Highlight Strongest Gravitational Field". The total number of fields affecting the character, i.e. candidates for being the strongest gravitational field, can be displayed above the character's head when "Show Affecting Fields Count" is enabled. 

## PP Controller Tools

In the editor menu "PP Controller Tools" at the top, you can find mass actions for drawing gizmos of all gravitational fields (and planets) in the scene. I recommend checking them out when building large, complex scenes to see what location is covered where by which planet. 