# Scene Setup

In the following, you find the steps for correctly setting up your own scene.

## Attaching the scripts

All scripts which are related to the character can be found inside Scripts > Character. Attach the scripts of your choice to your character game object, usually to its root game object:

1. **PPController:** Adding this component additionally adds the PPMotor and a Rigidbody component. While the PPController listens for user input via Unity's Input System (Input Actions can be found inside Scripts > Inputs), the PPMotor acts on them to move the character and fire animations. The PPMotor is based on the PPEngineObject component that takes care of all physics calculations. 
1. **PPCharacter:** Adding this component gives your object more character-like properties, e.g. the possibility to punch or shoot the equipped pistol to deal, but also suffer damage. This component automatically spawns a Capsule Collider if none was already found on the object.
1. **PPCamera:** Component for managing the camera according to the planet the character is currently walking on.

Of course, if you want to animate your character object, an Animator component is needed as well.

## Adding animations 

The asset provides an Animator Controller called "Character" with dummy animations that should make it easier to maintain and override it. Therefore, two additional Animator Overrides are provided on top – one for the character and one for the NPC. I recommend creating an own Animator Override and assigning this to your character's Animator component. If you are planning to import the [Astronaut Cartoony](https://assetstore.unity.com/packages/3d/characters/astronaut-cartoony-119965) package by Rheedo Animations that is also used for the asset showcase, override "CharacterOverride" will be automatically filled with the corresponding animations.

## Tagging your character (optional)

Tag your character object with "Player" if you plan to use the provided NPC AI (component "PPNpc"). Otherwise, NPCs would ignore the character and not interact with it.  

## Adding a planet to the scene

Go to the "Prefabs" folder and drag a prefab from "Planets" into the scene. The prefabs here already include a default ground surface, a gravitational field and camera settings. See section 2 for more information on how they work.

Now place your character object on the surface of the chosen planet and rotate it so that its feet point to the ground. Enter the play mode. 
