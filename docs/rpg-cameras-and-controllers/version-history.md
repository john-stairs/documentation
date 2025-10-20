# Version History

### v6.2

- Update to Unity 6000.0.58f2
- Bugfix: Materials without the maintained shader properties should no longer be processed
- Bugfix: Box colliders in the URP Playground demo should now be correctly aligned again
- Bugfix: Provided jump animation no longer loops 
- Trigger colliders are now also correctly recognized by the view frustum
- RPG Builder integration: Disable target lock on key press by default

### v6.1.3

General

- Upgrade to Unity 2021.3 (LTS)
- Minor updates to the written manual

RPGCamera

- The menu cursor no longer disables character movement

RPG Builder Integration

- Opening a UI panel no longer disables camera control in an MMO setup
- By default, the "UseRPGBuilderActionKeys" of the RPGControllerIntegration component is now disabled to avoid confusion
- Bugfix: Cursor Behavior "Stay" now properly triggers NPC interaction on the set up interaction distance
- Bugfix: Adjusted the provided integrated character prefabs so that no longer two components of type IPlayer are assigned. In some cases, this enabled control over the character even if it was not allowed
- Bugfix: Updated animations that were used by both assets to prevent collisions during import

### v6.1.2

- Bugfix: The legacy input name for the mouse scroll wheel should now be properly typed inside the RPGCamera script (thanks for reporting, Naked Fighter!)
- Bugfix: The FadeIn alpha of objects to fade is now properly reached in every case (thanks for reporting!)
- Bugfix: The Character Controller component is now a technical requirement of the RPGMotor scripts, i.e. it is added if it does not already exist on the same game object
- Bugfix: The motor script should no longer throw an error if there was no Animator component found
- The provided Utils method "IsPointerOverGUI" is now only checking for objects in layers of the passed layer mask (thanks for the feedback, Dan!)
- A warning is now logged in the console if there is no Input Action Asset assigned to the used Player Input component
- Added a playground demo scene with URP materials

### v6.1.1

- Bugfix: When Cursor Behavior "Stay" was selected, it could happen that character movement or camera rotation stopped when hovering over UI (thanks for the report, Law)
- Bugfix: If the character was strafing via Rotation and Rotation Modifier input and a UI panel was opened, the character continued to strafe instead of stopping
- Added a recommendation to the RPGBuilder README file about the "Toggle Menu Cursor" input action
- Handled animation errors that caused a floating character model (thanks for the support, Alexi!)

### v6.1

General

- RPGController and RPGCamera are now using Unity's PlayerInput component for easier management of input actions
    - As a result, you can now easily swap the provided input actions with your own
    - Additionally, you do not have to define all actions that were required for my scripts before. Missing actions will just cause the corresponding functionality to be disabled
    - There is a new button in each input handling script for checking the current input setup and logging the results to the console
    - Default Control Schemes "Keyboard + Mouse" and "Gamepad" are provided
    - The previously used RPGInputManager is no longer supported!
- Updated the manual that RPGPlayerExample also provides an example implementation of interface IPointerInfo to disable/enable asset controls when the cursor is over a UI element
- Asset includes now a dependency to Unity's Input System. This does not mean that its usage is mandatory. The legacy input system/manager can still be used as before
- Added missing materials of the capsules in the Playground demo scene

RPGMotor & RPGController

- New: Now uses Unity's PlayerInput component for input action handling (see corresponding item under "General")
- New: New public variable "SteadyAcceleration" for changing the maintenance of character acceleration to either time in seconds (current) or unit/s² (new) (thanks for the request!)
- New: Getter method for the current movement speed (thanks for the request!)
- New: Getter method for the current movement direction (thanks for the request, Law!)
- Bugfix: No longer race conditions between Controller and Motor initialization, e.g. in async scene (pre-)loading setups (thanks for reporting, pryankster!)
- Bugfix: Jumping out of the water should work again now properly
- Bugfix: The swimming animation is now properly played after sliding into the water from unwalable terrain (thanks for reporting, Shaq!)
- Bugfix: The MMO motor should no longer snap back to the horizontal plane when swimming
- Bugfix: ARPG motor midair movement via WASD is possibly again (thanks for reporting, Alex!)
- Bugfix: Swimming out of water boxes via surfacing or diving actions should now properly work again. The causing logic was disabled
- Refactoring of the interpretation of the RotationTime variable for the ARPG motor. Since it was in direct competition to variable AlignmentTime, it was removed to provide only a single variable for the purpose of controlling the time needed for the character to rotate to the target movement direction
- Extended the tooltip of the RunSpeed variable to make clearer that this is the default movement speed of the character

RPGCamera & RPGViewFrustum

- New: Now uses Unity's PlayerInput component for input action handling (see corresponding item under "General")
- New: Public variable "Pause [Alignment With Character] While Orbiting". If set to true, rotating the camera pauses camera alignment with the character. This is useful in situations where the character is locked on a target
- Bugfix: Dynamical assignment of the used camera is now implemented, i.e. later changes to the camera reference, e.g. due to async scene load, should be no problem anymore (thanks for reporting, pryankster!)
- Bugfix: The character no longer fades out earlier when zooming in very quickly (thanks for reporting, Law!)
- Bugfix: There is no longer an exception thrown when the script was initially disabled on the ARPG prefab
- Bugfix: Made the logic of material fade-out/in more robust (thanks for reporting, Wei!)
- Improved the RPGCameraEditor for smoothed pivots. The script parameters should no longer flicker between internal and external settings when pivot movement smoothing was enabled

RPG Builder Integration

- Bugfix: Input handling for action "CancelClimbing" was missing in the integrated controller scenario (thanks for reporting, Petr!)
- Bugfix: Animation transition for climbing was missing in the integrated animator (thanks for reporting, Petr!)

### v6.0

!!! warning
    This version introduces major breaking changes! It is recommended to stay at your current version if you do not need any of this version's new features or bugfixes. Always keep a version control or backup in place to be able to roll back your project to an earlier version in case of issues due to incompatibilities!

Large RPGCamera and RPGMotor refactoring

- Unified RPGCamera script: There is no longer a difference between the ARPG and the MMO camera
- Streamlined RPGMotors: Normalization of motor functionality, much leaner RPGMotorARPG and RPGMotorMMO components
- A single, enhanced Animator Controller
- Easier extensibility and maintainability
- Interfaces provided for each of the provided RPG scripts
- More user-friendly Editor scripts
- Unity's Input System is now used by default and usage of Unity's legacy input system, the Input Manager, has to be enabled explicitely by setting the corresponding public variable "UseLegacyInputSystem" to true

RPGMotor

- New: Ledge grabbing mechanic: Jump to ledges to grab them, move left and right along them and let go or climb up via input
- New: Free climbing mechanic: Move towards simple colliders to start climbing them. Climb in all directions and transition to ledge grabbing (if enabled as well)
- New: Crouching now also available for the MMO motor
- New: Strafing now also available for the ARPG motor
- New: In-place rotation now also available for the ARPG motor
- New: Public ARPG variable "AlwaysTurnToCursor" for letting the character always rotate towards the cursor (thanks for the request, Stefan!)
- New: Public variable "AccelerationTime" for defining the time needed until the target movement speed is reached (thanks for the request, Venzo!)
- New: Alignment with the camera view direction on input now also available for the ARPG motor
- New: Implementation of a "perfectly" timed jump mechanic for rewarding the player (thanks for the request!)
- New: Public method "GetCurrentState" for getting an Enum which represents the current motor state, e.g. Idle, Running, Jumping, Swimming (thanks for the request!)
- Bugfix: The jump animation is now always triggered when a jump at the water surface is performed
- Bugfix: The character is now immediately grounded at the start of the scene and not just after 1 or 2 frames
- Bugfix: Check routines now properly scale with the scale of the game object

RPGController

- New: Public variable "NormalizeInputValues" for normalizing player/controller input
- Bugfix: Input events are now properly consumed if controls are disabled

RPGCamera & RPGViewFrustum

- New: Camera shake effect with multiple new public variables and a simulation mode for easier setup (thanks for all the requests, everyone!)
- New: Camera follow behavior "Lazy" for a camera which only follows its pivot/character when it comes too close or moves too far away (see new prefab "EllenLazyARPG") (thanks for the request, William!)
- New: Public variable "SkipWaterSurface" for disabling/enabling the camera from continuously passing through water surfaces (thanks for the request, Joni!)
- New: The camera no longer zooms in completely when the frustum between the character and an external pivot is occluded
- New: Public variable "PivotSmoothTime" for smoothing pivot movement (also for internal pivots) (thanks for the request, Shaq!)
- New: Public variable "RelativeToCharacter" for setting if the start rotation should be relative to character transform or world transform (especially helpful in isometric setups) (thanks for reporting, Adam)
- New: "Toggle Menu Cursor" input for toggling a menu cursor, e.g. in case you have selected to always hide the cursor and need to enable/disable the cursor for UI interaction
- New: Public variable "OnlyIfLockedOnTarget" for aligning the camera with the character only if the character is locked on a target
- Bugfix: Orbiting behavior "Stay" no longer breaks when pressing and releasing LM and RM alternating (thanks for reporting, Joe!)
- Bugfix: Camera look up should now also properly work on very fast rotations
- Bugfix: The RotationSmoothTime is now also applied to the camera look up mechanic
- Bugfix: Method "MoveTo" should now work properly again
- Bugfix: Using layers for the camera look up mechanic should now work properly with all set up layers
- Bugfix: Objects now immediately fade out when the camera is forced to zoom in completely due to occlusion
- Bugfix: Input events are now properly consumed if controls are disabled
- Bugfix: Smooth transitioning is now also applied to the distance when using "SetPositionByParameters" method
- Improved cursor handling (bugfixes and less interferences)
- The ViewportMargin moved from the RPGViewFrustum to the RPGCamera
- Renamed "PivotSmoothTime" for smoothing the intelligent pivot movement to "IntelligentPivotSmoothTime" to prevent naming conflicts with the general pivot smoothing

### v5.5

RPGMotor

- New: Whenever the character is stuck due to (endless sliding), an anti-stuck mechanic is enabled. Public variable "AntiStuckTimeout" stores the corresponding time in seconds which need to pass before
- New: The character now immediately falls down when hit on the head during jumping
- Bugfix: The character should now again be moveable in Scene view while in play mode

RPGBuilder Integration

- New: Shapeshifting is now supported. Please use the Animator Controllers provided in the corresponding integration folder
- Bugfix: The cursor should now properly interact with GUI panels which are opened while in aiming mode

RPGCamera

- Refactored the cursor handling

### v5.4.2

- Bugfix: Disabling the aim feature for mounts in RPGBuilder no longer triggers a RPGCamera parameter reset

### v5.4.1

- Added code to the RPGCamera to prevent an incorrect setup of using "AlwaysRotateCamera" together with cursor behavior "Stay"

### v5.4

General

- Disabled Domain and Scene Reloading is supported now (Editor > Enter Play Mode Settings) (thanks for the request, Dale!)
- Provided more documentation about default return value of the ICharacterInfo interface methods
- Added experimental support for URP (Universal Render Pipeline) (thanks, Arcanor!)
- Added the arrow keys to the default key bindings for movement
- Minor housekeeping

RPGCamera

- New: Public variable "EnableUnderwaterEffect" for turning the underwater effect on/off
- Bugfix: Issue with the cursor handling when "AlwaysRotateCamera" and cursor behavior "LockInCenter" were used together
- Bugfix: No interference between enabled "AlwaysRotateCamera" and "AlignCameraWhenMoving" anymore
- Bugfix: Cursor visibility should now be correctly handled in all cases when activating and deactivating the camera control
- Cursor handling further optimized

RPGMotor

- New: Public variable "EnableSwimmingJumps" which controls if jumps while swimming at the water surface are possible
- Bugfix: Bumping into the water surface from below should no longer cause character jittering

RPGBuilder Integration

- New: Implemented the aiming feature
- Bugfix: It should no longer be possible to start while sliding down a slope

### v5.3.4

RPGBuilder Integration

- Bugfix: Jumping animation now correctly triggered while mounted (thanks for reporting, 3PO!)
- Bugfix: Animations while swimming should work properly now when mounted

### v5.3.3

RPGCamera

- Bugfix: Cursor y axis computation with cursor behavior "Stay" should now work correctly in builds for newer Unity releases (please write me the used Unity version if you are still affected!)

RPGBuilder Integration

- Implemented a workaround for stopping the casting animation after the cast has finished

### v5.3.2

RPGMotor

- New: Public method IsSliding for checking if the character is currently sliding or not (thanks for the request, Min!)
- Bugfix: Usage of interface method "CanMove" does no longer cause slowed falling

RPGBuilder Integration

- Mount support - please refer to the README for the additional setup step (thanks for your support, 3PO!)
- Added an animation state for flying without a mount

Misc

- Water bugfix: The global water level is now calculated independent of the local box collider position and scale (thanks, Joe!)

### v5.3.1

RPGBuilder Integration

- RPGViewFrustum error happening when equipped items are unequipped again should now be fixed (thanks for reporting, everyone!)

RPGCamera

- For external pivots, additional collider types are now supported: Capsule Collider, Box Collider and Sphere Collider (thanks for the idea, David!)

### v5.3

RPGCamera

- Bugfix: An enabled Intelligent Pivot does no longer interfere with the external pivot setup (thanks for reporting, wuqingman!)

RPGViewFrustum

- New: Object fading or camera look up can now also be triggered by script. Just assign the provided scripts FadeOut or CauseCameraLookUp, respectively, and you should be good to go. No dedicated tags or layers needed with this setting (thanks for the feature request, Wyldhunt!)
- Moved the initialization code to a better place

RPGMotor

- Users are now getting a warning if a conflict between the assigned layer and motor layermask IgnoredLayers was detected (thanks for the idea, Wyldhunt)

Integration

- A manual for simple integration with Mirror or similar networking libraries is now provided

General

- How to set up the water mechanics is now also part of the written manual
- Moved the third party assets folder into the asset's root directory (thanks for the hint, David)

### v5.2

RPGMotor

- Moving ground object logic is now decentralized. You now need to have the MovingPlatform script and a trigger collider assigned to the platform to have an effect onto the character. Please see section 1.2.6 of the manual or the new "Moving Platform" prefabs for more information!
- Movement due to collision works now much smoother than before

RPGBuilder Integration

- Regions are now correctly triggered (thanks for reporting, 3PO and Tony - btw. I could not reach you via mail: "Undelivered Mail Returned to Sender")
- Sprinting now properly stops when run out of stamina (thanks for reporting, Paul!)
- Casting while swimming was not possible if the ability had "Move and cast" disabled. This is now fixed (thanks for reporting, 3PO!)
- Animations are now only triggered for the upper body if the character is swimming or flying
- Other RPGBuilder animations like gathering or death added to the integrated animators. Unfortunately, I could not test them myself
- The replaced swimming animations should now also properly be included in the integrated animators

General

- The gizmo for visualizing the grounded check sphere is now drawn properly when jumping
- Minor housekeeping here and there

### v5.1.1

General

- Replaced the 2 swimming animations from Mixamo by animations which were kindly provided by Naked Fighter, thank you!

RPGMotor

- New public variable "Ignored Layers" for defining which layers are ignored by motor physics logic, i.e. not considered for the grounded check, sliding check, etc.

RPGCamera

- New public variable "Pivot Smooth Time" for smoothing the evasive movement of the pivot (intelligent pivot only)

### v5.1

RPGCamera

- Support of external pivot locations
- New "Intelligent Pivot" feature for internal pivots: The intelligent pivot automatically moves away from obstacles which the player could see through if zooming in enough
- ARP: Implemented a proper first person experience
- ARP: Start location setup is now relative to the character transform instead of world coordinates

RPGViewFrustum

- Implemented a second view frustum shape "Pyramid" with other strengths (and weaknesses) compared to the already implemented "Cuboid" shape
- For object fading, there is now also the possibility to select layers instead of tags
- For the camera look up, there is now also the possibility to select triggering layers instead of tags

RPGMotor

- Fixed the unnecessary animation firing when trying to swim above the surface

### v5.0.3

RPGBuilder Integration

- Leaping abilities should now work properly
- Fixed animator issues

### v5.0.2

RPGMotor

- New: Public variable "EnableCollisionMovement" for enabling/disabling collision movement. If set to true, the standing character is pushed away by moving objects on collision 

General

- Bugfix: Jumping is now properly disabled when character controls are disabled in the RPGController
- RPGBuilder integration: The character should no longer stick onto moving NPCs, when NPC collision is disabled (thanks for reporting, Joe "atoqed"!)
- Integrity check of ground leaping abilities postponed until Blink has fixed the issue on their end

### v5.0.1

RPGBuilder Integration

- Integrity check of ground leaping abilities postponed to after release of RPGBuilder v2.0.3

### v5.0

General

- This version contains major code restructurings and simplifications! Please be aware that breaking changes are highly likely if you extended my scripts!
- Asset rebranding to "RPG Cameras & Controllers" to better reflect the current content
- Renamed the camera and motor scripts of flavor "ThirdPerson" to "ARPG" because it better applies
- Integration of Unity's new Input System. The legacy Input Manager remains usable via deselecting "Use New Input System" on the corresponding input be developed for the new input system!
- Asset now shipped with Unity standard models and animations, kindly complemented by free animations by Blink Studios
- Revised demo scenes: MMO, ARPG, Isometric and Playgroud
- Simplified RPGBuilder integration. Note that integration is only supported for the most recent version of RPGBuilder!
- RPGBuilder integration: Added knockback support
- Revised debugging gizmos of the RPGCamera and RPGMotor

### v4.3.2

- New (RPGBuilder integration): Out-of-the-box integration with Blink Studio's RPGBuilder v1.1.0.8
- Bug fix (RPGBuilder integration): UI drag events are now recognized properly again
- Bug fix (RPGBuilder integration): Fixed file inconsistencies inside the unitypackages to import. Sorry for the inconvenience caused when reimporting them!

### v4.3.1

!!! bug
    Due to a bug in RPGBuilder v1.1.x, it is recommended to uncheck integration variable "UIPanelsDisableControls" until the release of RPGBuilder v1.1.0.8!

RPGBuilder Integration

- Bugfix: Respawn positions and teleports work properly again (thanks, Harris!)
- Bugfix: Leaping fixed
- Bugfix: Casting underwater fixed

### v4.3

RPGBuilder Integration

- New: Out-of-the-box integration with Blink Studio's RPGBuilder v1.1.0.7
- New: Public variable "EnableCameraMouseLook" for enabling/disabling the mouse look functionality (thanks, Malith!)
- New: Public variable "AlignCharacterWhenUsingAbility". If set to true, the character turns into the camera's facing direction when using/casting an ability (thanks, Malith!)
- New: Public variable "UIPanelsDisableControls". If set to true, character and camera controls are disabled as long as UI panels are opened

General

- New: Public variables for disabling the logged warnings of undefined project inputs
- New: Inputs used by the scripts are now shipped via Input Manager preset
- Bugfix: Small adjustment of the camera look up logic inside the RPGViewFrustum
- Variable and method visibility changes in all scripts (thanks, Marc!)
- Added an additional setup step for the RPGBuilder integration so that the camera look up also consistently works in the RPGBuilder demo

### v4.2.1

- New: Out-of-the-box integration with Blink Studio's RPGBuilder v1.1.0.5
- Fixed a bug with the RPGBuilder v1.1 integration

### v4.2

- New: Public RPGMotor variable "EnableMidairJumps" and "AllowedMidairJumps" to allow jumps while the character is in midair, e.g. double jumps
- New: Public RPGMotor variable "EnableMidairMovement" to set up when midair movement is allowed, e.g. never, only after a standing jump or always
- New: Public RPGMotor_ThirdPerson variable "SmoothDirectionInputChanges" for enabling smoothing of input direction changes when a keyboard is used (Input.GetAxis vs. Input.GetAxisRaw)
- Updated the integration code for Blink Studio's RPGBuilder to work with its newest version
- Minor code optimization and housekeeping

### v4.1

- New: Out-of-the-box integration with Blink Studio's RPGBuilder. Just import the provided unitypackage in directory "Integration > RPGBuilder" - no manual code changes required anymore!
- New: Public RPGViewFrustum variable "EnableCameraLookUp" for enabling/disabling the camera look up functionality when touching the terrain
- New: Public RPGViewFrustum variable "ViewportMargin" for setting up margins for the viewport in x and y direction
- New: RPGCamera methods GetPosition() and SetPosition() for retrieving and setting the current camera position
- Bugfix: Method TeleportTo() of the ThirdPerson motor now correctly rotates the character if parameter "withYrotation" is passed as true
- Bugfix: The camera look up functionality works now also if no RPGMotor script was found on the same game object
- Minor housekeeping

### v4.0.1

- Bugfix: The moving/rotating ground mechanic should now also work properly in very special cases. Thanks, Richard, for reporting this bug and reproducing it for me!
- Bugfix: The mechanic behind public variable "GroundAffectsJumping" is now working properly again 
- Bugfix: Removed duplicate display of variable "AlwaysRotateCamera" in the RPGCameraEditor scripts
- Removed the remains of the default inputs inside descriptive variable names to be consistent

### v4.0

New Features

- Added separate RPGController, RPGMotor and RPGCamera scripts and a dedicated Animator Controller for modern RPG Third Person character and camera controls. You can try them out in demo preset "3rd Person". The original scripts were renamed to end with "_MMO", whereas the new scripts end with "_ThirdPerson"
- Introducing a new, more advanced Animator Controller for the MMO scripts
- Easier integration for third-party input systems via method GetInputs() in each controller and camera script
- RPGCameraEditor and RPGMotorEditor scripts for easier variable handling in the inspector
- IRPGMotor interfaces which are implemented by the RPGMotor scripts to get an easier overview of the provided motor methods, e.g. for implementing your own controller or AI
- Additional demo scene "3rd Person" with the new Third Person camera and controller

Changes & Improvements

- Code optimizations and simplifications in the RPGMotor_MMO script
- Code optimizations and simplifications in the RPGCamera_MMO script
- Rework of the first 3 demo scenes introducing a new character model
- RPGMotor_MMO input "Horizontal Strafe" renamed to "Strafe"
- Public RPGMotor variable "RotationSpeed" now represents the approximate turning degrees per second to make it more intuitive
- Public RPGMotor variable "JumpHeight" now really represents the jump height in world units
- Public RPGMotor variable "SlidingThreshold" renamed to "SlidingAngle"
- Public RPGCamera variable names that contained the term "Mouse" are now named according to their functionality instead of their corresponding default input
- Public RPGCamera variables "InvertRotationX" (previously "InvertMouseX") and "InvertRotationY" (previously "InvertMouseY") are now defined more intuitively with respect to mouse movement instead of just representing the technical view
- Public MMO Enum value "RotateWithCharacter.RotationStoppingInput" was renamed to "RotateWithCharacter.PreventOnInput"
- Bugfix: Game objects which are destroyed while entering or leaving the RPGViewFrustum no longer throw Exceptions

### v3.7.3

- Updated support for Unity 2020
- Introduced new PRGMotor method "TeleportTo(target, withYrotation)" which teleports the character to Transform target. Optional bool parameter withYrotation triggers additional alignment of the character's Y axis rotation
- Fixed a bug which sometimes caused the character to remain tilted after jumping out of the water
- Introduced new RPGMotor method "ResetXaxisRotation()" which immediately resets the X axis rotation of the character
- Introduced new RPGController variable "ActivateCharacterControl" which enables/disables controller input
- Fixed a bug with the demo GUI which sometimes caused the cursor to jump to the center of the screen when GUI elements were clicked
- Integrated the new RPGController variable "ActivateCharacterControl" into the demo so that typing in input fields does not trigger character movement
- Added an own namespace to the asset scripts

### v3.7.2

- Implemented fallback routines for the features "Move with moving ground", "Rotate with rotating ground" and "Ground object affects jump" in case the project physics setting "Auto Sync Transforms" is turned off.

### v3.7.1

- Created dummy animations and assigned them to the Animator Controller so that the demo settings are not lost. Note that the "Mirror animation" checkbox has to be set manually after replacing the dummies
- Added an animation mapping table to the manual to easier find out which Mixamo animation was used for which motion in the demo

### v3.7

New Features

- Introduced new feature: Swimming
- Introduced new RPGMotor variable "Swim Speed Multiplier". Defines the multiplier which is applied to the character movement speed when the character is swimming
- Introduced new RPGMotor variable "Swimming Start Height". Defines the local water height at which the character should start to swim. Gizmo available for easier setup
- Introduced new RPGMotor variable "Dive Only When Swimming Forward". If set to true, the character starts to dive only when moving forward (or backwards). Otherwise, the character remains in an upright stance
- Introduced new RPGCamera variable "Underwater Fog Color". Defines the fog color which should be applied when the camera below the water surface
- Introduced new RPGCamera variable "Underwater Fog Density". Defines the fog density which should be applied when the camera below the water surface
- Introduced new RPGCamera methods "EnableUnderwaterEffects()" and its counterpart "DisableUnderwaterEffects()". Enables/disables the visual underwater effects which should be applied once the camera is below water surface. Use these two methods to implement your own visual effects
- Introduced new RPGCamera variable "Underwater Threshold Tuning". Gives the possibility to fine-tune the threshold where the camera is seen as underwater. The higher the value, the earlier the underwater effects kick in

Changes & Improvements

- Complete overhaul and simplification of the provided Animator Controller
- New demo with character model and new animations
- Fixed camera jittering which sometimes occurred when the character was aligning with the camera
- If the character is stunned, the camera can now continue to orbit around the character with RM or the alignment input pressed
- Added the possibility to stun the character during the demo (button 'T')
- Minor code optimizations
- Updated to the newest Unity stable release

### v3.6

- Introduced new RPGMotor variable "Unlimited Airborne Moves". If set to true, the number of allowed moves while airborne is unlimited
- Introduced new RPGMotor method "Stun(duration)" which stuns the character for "duration" seconds, disabling movement and transitioning into the new "Stunned" animator state
- Introduced new RPGCamera variable "Align Character Speed" which controls the character-to-camera turning speed
- Character fading now correctly depends on the distance between the camera and the character
- Small logical adjustments

### v3.5

- Introduced new RPGMotor variable "Move With Moving Ground". If set to true, the character will stay on moving objects like moving platforms
- Introduced new RPGMotor variable "Rotate With Rotating Ground". If set to true, the character will rotate with rotating objects while standing on them
- Introduced new RPGMotor variable "Ground Object Affects Jump". If set to true, the jumping direction gets affected by the (moving) object the character was standing on
- Introduced new RPGCamera variable "Rotation Stopping Input" for setting which input should be pressed to pause automatic camera rotation with the character (only usable if "Rotate With Character" is set to "Rotation Stopping Input")
- Introduced new RPGCamera variable "Alignment Input" for setting which input should be pressed to align the character's view direction with the camera view direction (only usable if "Align Character" is set to "On Alignment Input")
- Updated the demo scenes for the new features
- Updated the GUI layout
- Updated the manual for using the RPGCamera with Unity's ThirdPersonController standard asset
- Minor bugfixes

### v3.4

- Fixed a bug when the RPGController and RPGCamera were used independently
- Added instructions to the Documentation folder for using the RPGCamera with Unity's ThirdPersonController standard asset
- New RPGCamera variable "Rotate With Character" which lets you set if the camera should rotate as well when the character turns
- Minor code additions and changes

### v3.3

- When LM is pressed, the camera does not rotate with the character anymore
- When jumping into objects from below, the character bounces off immediately
- Introduced new RPGCamera variable "Support Walking Backwards" for better character alignment when walking backwards
- Improved the provided demo shader
- Fixed a bug where it was possible to turn the camera upside down in first-person mode

### v3.2

- Fixed a bug in first person view which caused the camera to behave incorrectly
- Fixed a bug where it was possible to force the camera under terrain for a few frames
- Added the possibility to group the RPGCamera script variables in the inspector

### v3.1

- Fixed an animation bug in the demo caused by Unity's new editor version 5.1.1f1
- Improved interleaving of scripts
- Improved RPGController and RPGMotor scripts
- Implemented a better approach for camera rotation
- Introduced new RPGCamera variables:
    - Used Skybox
    - Constrain Mouse X
    - Mouse X Min
    - Mouse X Max
- Moved the variable "Align Character With Camera" to RPGCamera and renamed it to "Align Character" to improve readability and efficiency
- Updated manual instructions

### v3.0

- Added animations controlled by Mecanim
- Added a walking toggle
- Object fading between the camera and its pivot
- Different occlusion handling modes selectable
- Tag dependent camera zoom enforcement (easy setup in the inspector)
- Slower backwards walking if desired
- 21 new public variables for easier and more customization
- New GUI for the demo
- Replaced the RPGClipPlane by the RPGViewFrustum and moved view frustum computations there
- Removed a bug where you could jump while sliding resulting in greater jumps

### v2.1

- Update for Unity 5

### v2.0

- Complete revision
- Huge amount of new controller and camera features added
- UML diagram included
- Let out the animation scripting

### v1.1

- Added the "RPG_Animation" script
- Added a capsule model with animation clips attached to it
- Changed object hierarchy of the "PlayerChar" object
- The cursor is not locked anymore if you press the left mouse
- New public variable "fallingThreshold" in "RPG_Controller" defining the terrain height at which the character starts to stumble
- Setting the layer of PlayerChar to "Ignore Raycast" is not necessary anymore
- Some code and names improved/edited for clearer

### v1.0

- Release