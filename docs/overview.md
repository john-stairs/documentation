# Overview

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

!!! info

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

<div style="text-align:center"><img src="img/left.jpg"/></div>

## Feature matrix

| Feature | RPG Camera Lite | RPG Camera | RPG Cameras & Controllers |
| --- | --- | --- | --- |
| **Camera** |     |     |     |
| Arbitrarily smooth orbit camera | ✅   | ✅   | ✅   |
| Seamlessly transition between third- and first-person view | ✅   | ✅   | ✅   |
| Intelligent occlusion handling: |     |     |     |
| └ Choose out of two shapes of view frustums: pyramid or cuboid | ✅   | ✅   | ✅   |
| └ Decide which objects cause immediate zoom in | ✅   | ✅   | ✅   |
| └ Decide which objects should fade out instead of causing a zoom in | ❌   | ✅   | ✅   |
| └ Set the fade out and fade in alpha as well as the fading duration | ❌   | ✅   | ✅   |
| └ If there is no occlusion anymore, the camera automatically zooms out to the desired distance | ✅   | ✅   | ✅   |
| Enable/disable character fading and set the starting and ending distance as well as the maximum fade out alpha value | ❌   | ✅   | ✅   |
| Support of internal and external camera pivots, i.e. within the character collider or not | ❌   | ✅   | ✅   |
| Evasive pivot that moves away from obstacles which the player could see through if zooming in enough | ❌   | ✅   | ✅   |
| Cursor hiding - never, always or only when orbiting | ✅   | ✅   | ✅   |
| Dedicated cursor behavior while orbiting - move, lock in center or stay | ❌   | ❌   | ✅   |
| Possibility to align the character with the camera's view direction | ❌   | ❌   | ✅   |
| Possibility to control when the camera should rotate together with the character | ✅   | ✅   | ✅   |
| Turn on/off automatic alignment with the character when it is moving (with support for walking backwards) | ✅   | ✅   | ✅   |
| Following behaviors "Strict" and "Lazy" | ❌   | ❌   | ✅   |
| Movable camera pivot | ✅   | ✅   | ✅   |
| Camera look up if it lies on objects that have a dedicated tag assigned | ❌   | ✅   | ✅   |
| Lock a rotation axis or set a maximum angle | ✅   | ✅   | ✅   |
| Axis input inversion | ✅   | ✅   | ✅   |
| Minimum and maximum distance individually adjustable | ✅   | ✅   | ✅   |
| Fast first person zoom and maximum distance zoom at the touch of a button | ✅   | ✅   | ✅   |
| Underwater effects | ✅   | ✅   | ✅   |
| Water level skip | ❌   | ✅   | ✅   |
| Camera shaking effect | ✅   | ✅   | ✅   |
| Unity's Input System support | ✅   | ✅   | ✅   |
| Unity's legacy Input Manager support | ❌   | ❌   | ✅   |
| ...and more |     |     |     |
| **Character Controller** |     |     |     |
| Choose from 2 RPG controller flavors: |     |     |     |
| └ MMO (e.g. World of Warcraft) | ❌   | ❌   | ✅   |
| └ ARPG/Third Person (e.g. Zelda BotW or The Witcher) | ❌   | ❌   | ✅   |
| Large set of different motions: running, walking, crouching, sprinting, strafing - all with adjustable movement speed values or multipliers | ❌   | ❌   | ✅   |
| Swimming and diving mechanics | ❌   | ❌   | ✅   |
| Ledge and Free Climbing mechanics | ❌   | ❌   | ✅   |
| Set jump height and applied gravity | ❌   | ❌   | ✅   |
| Allow an arbitrary number of midair jumps | ❌   | ❌   | ✅   |
| Reward perfect midair jumps at their peak | ❌   | ❌   | ✅   |
| Allow an arbitrary number of moves and their speed in midair - never, always or only after a standing jump | ❌   | ❌   | ✅   |
| Toggle intelligent autorunning which can be turned on while running and turned off again on manual input | ❌   | ❌   | ✅   |
| Turn on/off if the character should move and rotate with the object it is standing on | ❌   | ❌   | ✅   |
| Also enable/disable if those objects affect jumping, i.e. always landing on the same point after a standing jump | ❌   | ❌   | ✅   |
| Sliding mechanics with adjustable angle when the character should start to slide | ❌   | ❌   | ✅   |
| Flying mechanic | ❌   | ❌   | ✅   |
| Adjustable tolerance of grounded checks, e.g. for running over debris | ❌   | ❌   | ✅   |
| Falling threshold | ❌   | ❌   | ✅   |
| Mecanim animator controller for every implemented action | ❌   | ❌   | ✅   |
| Unity's Input System support | ✅   | ✅   | ✅   |
| Unity's legacy Input Manager support | ❌   | ❌   | ✅   |
| ...and more |     |     |     |
