# Version History

### v2.0

!!! warning
    This version introduces major breaking changes! It is recommended to stay at your current version if you do not need any of this version's new features or bugfixes. Always keep a version control or backup in place to be able to roll back your project to an earlier version in case of issues due to incompatibilities!

Large refactorings

- The Planet Platformer Engine that is mainly responsible for the physics calculations affecting objects, including characters, was completely reworked
- As a result, the new PPMotor and NPC scripts were built up from scratch with easier extensibility and maintainability in mind. A new PPCharacter script is introduced with new out-of-the-box features
- Moreover, the planet modeling and camera management was simplified with a stronger focus on usability
- More user-friendly Editor scripts for all components
- Usage of Unity's Input System
- Disabled Domain and Scene Reloading is supported now (Editor > [Enter Play Mode Settings](https://docs.unity3d.com/Manual/ConfigurableEnterPlayMode.html))

PPMotor

- New: Public variable "AccelerationTime" for specifying the time in seconds to reach the target speed, e.g. from standing to running
- New: Public variable "EnableTripleJump" for enabling/disabling the triple jump
- New: Public variable "TimeForConsecutiveJump" for specifying the time the player has to perform a double/triple jump after landing
- New: Public variables for jump height multipliers depending on the performed jump
- New: Public variables for defining the jump height and distance of the backflip and side somersault (the latter can also be enabled/disabled on demand)
- More variables for tweaking physics
- Bugfix: The instant turnaround/U-turn can no longer be triggered multiple times in the same spot
- Bugfix: The instant turnaround/U-turn can no longer be triggered after landing, e.g. from a jump or planet change

PPController

- Uses Unity's Input System now. The previously used legacy input management is no longer supported
- Additionally covers the non-related character input for the new PPCharacter component

PPNpc

- Removed the complex state machine and implemented a simple but powerful NPC logic including random wandering spots and aggro radius mechanic
- Shared animator controller with the PPMotor and PPCharacter, working with Animator Overrides

PPEngineObject

- PPCollider component was thrown away and replaced by a more generic solution based on Unity's Collider class
- New: Event "ChangingPlanet" for signalizing a transition of the object from one to another planet
- The "Planet" concept was reworked (see new component below) and the corresponding layer was renamed to "Ground" to represent colliders the character can walk on
- More variables for tweaking physics
- Bugfix: Game object scaling should now be properly handled
- Updated gizmos for easier traceability

PPCharacter

- New component for character related logic, like controlling immovability, health or death
- In addition to the already existing punch, the character can now also shoot with a pistol:
  - New component "Pistol" representing a pistol that the character can use to fire the assigned projectile prefab after a specified time to aim
  - New component "Projectile" for defining the movement speed, force and damage on impact for a pistol shot. The projectile is itself a PPEngineObject and therefore affected by the engine's physics
- New: Public variables "HaltWhenPunching" and "HaltWhenPunchingDuration" for specifying if the character should stand still when performing a punch and - if yes - for how long
- New: Public variable "AttackCooldownDuration" for setting the cooldown of attacks like punching or shooting
- New: Public variable "RecoveryTime" for specifying the time in seconds the character needs to stand up/move again after being hit
- Example UI prefab for a health bar
- New gizmos for visualizing the set up punch parameters, e.g. punch height, radius and range

PPCamera

- The whole camera management was redesigned. There are no longer "CameraSettings" objects or prefabs that need to be assigned to a object in a scene representing a planet
- Camera behaviors/settings are now maintained via the new planet component
- The PPCamera script itself now only contains a reference to the camera that should be used. By default, the Main Camera is used if nothing is assigned

Planet

- New component for marking a game object as a planet that comprises a camera behavior/setting, and all gravitational fields and "Ground" colliders in its children
- 6 camera settings to choose from per planet (try them out in the new demo)
- Editor script with full transparency on each object that makes up the planet

Demo

- New demo "Level" showing the majority of features in a single scene
- 6 new demo scenes, each presenting one of the reworked camera behaviors/settings. This makes it easier for you to decide which camera setup fits your planet best

### v1.4

- New: PPMotor variable "StickToSurface" which controls if the character should align with the planet surface or with the gravitational field lines. Only applies when the character is grounded
- New: Easier integration for third-party input systems via method GetInputs() in each input-handling script
- Updated the "Planet" layer section of the manual with a hint for running the provided demos in a project that already had custom layers set up (Thanks, Ricky!)
- Fixed a bug in demo 3 where sometimes changing the input direction did not cause a change in movement direction. Also tagged the center pillar correctly as a planet

### v1.3.1

PPMotor Improvements

- PPMotor code rework and simplification for better readability, e.g. by completely removing the planet change mechanic and restructuring methods. The previous PPMotor script version is still provided with this asset as PPMotor_old but will be removed with the next major update

New Features

- PPEngineObject script which comprises all methods needed for leveraging the physics engine of this asset. Just extend this class (like the PPMotor or PPSimpleObject) and you will have all the physics methods you need
- PPSimpleObject script which extends PPEngineObject that represents a minimum example of this asset's physics. The corresponding prefab Simple Object is used in demo one for the falling cubes
- PPCollider script which is essentially a Collider component wrapper for supporting different collider types inside the PPMotor
- The PPMotor does now also support a box collider instead of the capsule collider
- Interface I_PPMotor which is implemented by the PPMotor. The purpose of this interface is mainly for documentation, e.g. for implementing an own controller or to check which methods/internal data can be retrieved from outside the PPMotor
- Inserted a rotation during ledge climbing for ledges with more than 40 degrees (default value) so that it works properly and looks more natural

Changes & Bugfixes

- Ledge grabbing debug rays are now only drawn if ledge grabbing is enabled for the character
- GravitationalField – Capsule variable "DisableCapFields" which disables the radial fields at both ends of the capsule collider if set to true. An example can be seen in the Vert Ramp Down prefab (demo 2)
- Bugfix: Method "PerformAttack" now correctly ignores trigger colliders
- Bugfix: Triggering an attack while midair does not lead to a call of "PerformAttack" once the character is grounded again
- Bugfix: It is no longer possible to perform multiple quick turnarounds on the spot
- Bugfix: The possibility to do a quick turnaround on the spot right after the character landed was removed
- Bugfix: In some cases after a quick turnaround, the character did not turn into the exact opposite direction when giving the corresponding input. This has been fixed now

### v1.3

New PPMotor Features

- PPMotor ledge grab and ledge climbing mechanic implemented
- PPMotor attack mechanic for the character implemented
- PPMotor quick turnaround mechanic implemented. Whenever the character is running and an input into the opposite direction is given, the character performs a quick turnaround on the spot
- PPMotor side flip mechanic implemented. Pressing the jump input during a quick turnaround triggers a side flip
- New Animator states for ledge grab, ledge climbing, quick turnaround and side flip
- New PPMotor variables:
  - AllowSideFlip
  - SideFlipForceMultiplier
  - QuickTurnaroundDuration
  - AllowLedgeGrabbing
  - LedgeGrabHeight
  - LedgeGrabRange
  - LedgeMaxAngle
  - AllowLedgeClimbing
  - LedgeClimbingSpeed
  - AttackRange
  - AttackCooldown
  - DamageOnBodyContact
  - ContactDamage
  - BodyContactForce

Other Improvements

- New: PPNpcAI script replacing the PPNpcController script. The script was completely rewritten to follow a state-of-the-art finite state machine logic. Additionally, simplifications and restructurings have been conducted to better integrate into the PPMotor
- New: NPC Animator revision in accordance with the new PP NPC AI script
- New: CameraBehavior Static3D where the camera sits on one of the 6 world axes and automatically jumps to the world axis to which the character game object is closest
- New: CameraBehavior Static3DLookAtCharacter
- New: Camera component added to the CameraSettings prefab for easier view setup
- New: CameraSettings variable "CopyCamCompValues" to copy the values of the assigned camera component
- New: PP Controller Tools menu item in the editor for drawing additional PPMotor gizmos or hide/show gravitational fields
- Bugfix: the routine in PPMotor for preventing the character from being stuck on a ledge works now properly only on bottom contacts
- New: PPMotorEditor script for a structured PPMotor presentation in the inspector
- Renamed PPMotor variable "BackflipSpeedMultiplier" to "BackflipForceMultiplier"
- Renamed PPMotor variable "AttackForceVector" to "AttackForceDirection"
- Further PPMotor simplifications, e.g. removing the NPC Motor flag or AttackType
- Renamed CameraSettings variable "FollowDistance" to "Distance"
- Minor code adjustments here and there

### v1.2

PPCamera

- PPCamera code rework and improvements, e.g. smoother transition between different camera settings and more intuitive setup
- Removed the PlanetSurface script to support an easier camera setup (new mechanic explained in the manual)
- New: PPCamera variable "SecondsToTransition" for setting the time in seconds needed for transitioning from the current to a new camera setting
- New: PPCamera variable "TransitionRotationDelay" for setting the delay in seconds after the camera starts to rotate to a new camera setting
- New: CameraBehavior FollowCylindrical with its own new Camera Settings

PPMotor

- New: PPMotor variable "GroundedCheckRayLength" to change the length of the ray which checks if the character is grounded or not
- New: PPMotor variable "DirectInput" for enabling/disabling if the controller input is always and directly used to determine the new movement direction of the character
- New: PPMotor variable "MaxTurningDegreesPlanetChange" for setting the maximum degrees the character rotates per FixedUpdate call while changing/flying to another planet
- New: Added bool "Changing Planet" to the Animator to be able to check if the character is currently changing to another planet, e.g. for transitioning to an extra animation

Updates & Fixes

- Updated demo 2 with a capsule planet which uses the capsule gravitational field from last release
- New demo 3 which uses the new CameraBehavior FollowCylindrical
- Updated demo 4
- The collider detection of the gravitational fields does now properly work with multiple different colliders
- Minor code optimizations and bug fixes

### v1.1

Updates

- Updated support for Unity 2020
- New: PPMotor variable "MovementDirChangeSmoothTime" for setting the time the character needs to rotate into the new movement direction. The greater the value, the greater the arc the character runs when changing direction. Only exceptions are movement changes into the opposite direction which remain on the spot
- New: PPMotor variable "MovementStartSmoothTime" for setting the time the character needs before reaching the maximum movement speed when starting from a standing position
- New: PPMotor variables "AllowHorizontalMovement" and "AllowVerticalMovement" for enabling/disabling the horizontal and vertical character movement
- New: PPMotor variable "AllowJumping" for enabling/disabling character jumping
- New: Gravitational Field variables "ShowField" and "FieldColor" for showing/hiding the gizmo of the corresponding field and setting its color
- New: Gravitational field in the shape of a capsule, e.g. for cylindrical planets or objects like the vertical ramp down

New Content

- New: Prefab "Vertical Ramp Down" (used in Demo 3)
- New: Prefab "Vertical Ramp" (used in Demo 3 and 4)
- New: Example capsule planet
- New: Demo 3 as an example for a more complex side-scroller scene and for showing possible usages for the new prefabs
- New: Demo 4 for testing the vertical ramp prefab

Bugfixes

- Bug fix: The calculation of the movement direction works now correctly when the character's Y axis is close to the camera's X axis
- Bug fix: Jumps above convex terrain now always have the same distance and do not behave differently anymore
- Bug fix: The jump animation is now properly cancelled when changing between close platforms
- Bug fix: The character's walk animation is no longer stuck in the demos

Other Changes

- Added the required components Rigidbody and Capsule Collider to the PPMotor script
- Added an own namespace to the asset scripts

### v1.0

- Release