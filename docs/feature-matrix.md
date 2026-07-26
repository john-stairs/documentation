# Feature matrix for RPG assets

| Feature | RPG Camera Lite | RPG Camera | RPG Character Controllers |
| --- | --- | --- | --- |
| **Camera** |     |     |     |
| Arbitrarily smooth orbit camera | ✅   | ✅   | ✅   |
| Seamlessly transition between third- and first-person view | ✅   | ✅   | ✅   |
| Intelligent occlusion handling: |     |     |     |
| └ Choose out of two shapes of view frustums: pyramid or cuboid | ✅   | ✅   | ✅   |
| └ Decide which objects cause immediate zoom in | ✅   | ✅   | ✅   |
| └ Decide which objects should fade out instead of causing a zoom in | ❌   | ✅   | ✅   |
| └ Set the fade out alpha and fade in/out duration | ❌   | ✅   | ✅   |
| └ Camera automatically zooms out to the desired distance if there is no occlusion anymore | ✅   | ✅   | ✅   |
| Enable/disable character fading, set the start and end distance and the maximum fade out alpha value | ❌   | ✅   | ✅   |
| Support of internal and external camera pivots, i.e. within the character collider or outside | ❌   | ✅   | ✅   |
| Evasive pivot that moves away from obstacles which the player could see through in first-person mode | ❌   | ✅   | ✅   |
| Hide cursor at position when orbiting | ✅   | ✅   | ✅   |
| Control if the camera should rotate together with the character | ✅   | ✅   | ✅   |
| Alignment with the character during movement (with support for walking backwards) | ✅   | ✅   | ✅   |
| Movable camera pivot | ✅   | ✅   | ✅   |
| Camera look up if it lies on objects that have a dedicated tag assigned | ❌   | ✅   | ✅   |
| Lock a rotation axis or set a maximum angle | ✅   | ✅   | ✅   |
| Axis input inversion | ✅   | ✅   | ✅   |
| Minimum and maximum distance individually adjustable | ✅   | ✅   | ✅   |
| Fast first person zoom and maximum distance zoom at the touch of a button | ✅   | ✅   | ✅   |
| Underwater effects | ✅   | ✅   | ✅   |
| Water level skip | ❌   | ✅   | ✅   |
| Camera shaking effect | ✅   | ✅   | ✅   |
| ...and more |     |     |     |
| **Character** |     |     |     |
| Choose from multiple RPG controllers: |     |     |     |
| └ MMO (e.g. World of Warcraft) | ❌   | ❌   | ✅   |
| └ ARPG/Third Person (e.g. Zelda BotW or The Witcher) | ❌   | ❌   | ✅   |
| └ Isometric (e.g. Hades) | ❌   | ❌   | ✅   |
| Large set of different motions: running, walking, crouching, sprinting, strafing - all with adjustable movement speed values or multipliers | ❌   | ❌   | ✅   |
| Swimming and diving mechanics | ❌   | ❌   | ✅   |
| Flying mechanics | ❌   | ❌   | ✅   |
| Ledge and free climbing mechanics | ❌   | ❌   | ✅   |
| Sliding mechanics with adjustable angle when the character should start to slide | ❌   | ❌   | ✅   |
| Target/combat lock mechanic | ❌   | ❌   | ✅   |
| Moving platforms (carriers) | ❌   | ❌   | ✅   |
| Enable/disable if carriers affect jumping, i.e. always landing on the same point after a standing jump | ❌   | ❌   | ✅   |
| Alignment with the camera's view direction on input | ❌   | ❌   | ✅   |
| Set jump height and applied gravity | ❌   | ❌   | ✅   |
| Allow an arbitrary number of midair jumps | ❌   | ❌   | ✅   |
| Allow midair movement | ❌   | ❌   | ✅   |
| Intelligent autorunning which can be turned on while running and turned off again on manual input (like in World of Warcraft) | ❌   | ❌   | ✅   |
| Adjustable tolerance of grounded checks, e.g. for running over debris | ❌   | ❌   | ✅   |
| Adjustable ground stickiness | ❌   | ❌   | ✅   |
| Mecanim animator controller for every implemented action | ❌   | ❌   | ✅   |
| ...and more |     |     |     |
