# Physics engine

On this page, the implemented physics engine and its mechanics are explained. Usually, this in-depth knowledge is not needed if you are just using the provided prefabs. The goal is to provide knowledge to everyone who is interested, and make scene creation easier despite the engine's complexity. If any aspect is not simple enough described or missing, please contact me so I can improve the documentation. 
In the following, the term "character" is used instead of the more general term "engine object". A character is an engine object, but an engine object is not necessarily a character. See for example the prefab "Simple Object" with component "PP Simple Object that inherits from script "PP Engine Object".

## The "Ground" layer

All game objects that are assigned to the "Ground" layer are considered as surfaces the character can walk on. The character's "Grounded Check" only considers objects of this layer. Based on Unity's physics engine, these objects need to have colliders for collision detection. Note that Unity's Terrains are only rudimentary supported due to their high triangle count (leads to more surface variance and bumpiness). You can check the Terrain game object with disabled collider in demo scene "Level" if you are interested in an example.

## Gravitational fields

Gravitational fields play a vital role in the physics computations. They are game objects that consist of a Unity collider component and a gravitational field script. The former is set up as a trigger, the latter is distinguished as spherical, uniform or capsule. As the name suggests, spherical fields have a gravity vector towards their center, whereas the uniform fields' gravity vector always points into the same direction. The capsule field is a combination of both. You can enable gizmos for visualizing the field and its field lines per gravitational field.

Each gravitational field has a priority and a gravity value. Gravitational fields with higher priority always overrule other fields with lower priority. The stronger the gravity of a field, the faster the character is drawn towards the object of layer "Ground".

At every time, there is at most one gravitational field physically affecting the character object – it is the strongest gravitational field. If the character is not affected by any gravitational field for the number of seconds stored in public variable "Lost In Space Time Threshold", it is considered as lost in space.

## Strongest Gravitational fields

The strongest gravitational field is picked from all the fields which could currently affect the character, i.e. all field trigger colliders which contain the character object. Generally, a field with a higher priority wins over the other. If the priorities are the same, for each field a ray is cast from the character along the field lines detecting only hits with objects which have the "Ground" layer assigned. The Ground object whose surface is closest to the character game object wins. Note that this means that grounds and gravitational fields can act independently. After a strongest gravitational field is found, the gravity vector of that field is applied to the character game object. The direction of the gravity vector results from the field lines multiplied by the field's gravity.

!!! note    
    As the range and therefore the influence of a gravitational field depends on the attached collider size, it is recommended to leave the collider component scales to 1 and scale the whole gravitational field prefab instead for convenience.

## Character alignment

If the character is not grounded and a strongest gravitational field is found, the field's gravity vector at the position of the character is taken and a ray is cast in its direction. The character's up vector is then aligned with the normal vector of the hit Ground collider. 

If the character is grounded and variable "Stick To Surface" is checked, the character stays aligned with the ground surface it is currently walking on. As a result, it is possible to run up vertical ramps as long as they have a smooth ground transition.

## Planets

Planets consist of ground objects, i.e. objects on layer "Ground", and gravitational fields. A planet can have multiples of both. Planets can be simple objects like the provided prefabs inside folder "Planets" or complex with multiple ground objects and many gravitational fields. However, it is generally not recommended to overlap two different types of gravitational fields within one planet. If needed and depending on the use case, side effects can sometimes be overcome via assigning different field priorities. 

To group ground and gravitational field objects into one planet, unite them under a single root/parent object and assign the "Planet" component to it. Then, all children are together considered as one planet. Why is this important? Planets should represent smoothly connected objects that form something bigger. No transition logic is applied when the character travels through the fields of one planet. On the other hand, if the new strongest gravitational field is from another planet, the "change planet" logic kicks in and the character is aligned and moved to the new planet ground object.

## Camera settings

Each planet object can have its own set of Camera Settings that are represented by a single component on the same object as the planet script. This component stores the camera behavior, generally position and rotation, which is applied when the character lands onto this planet.

There are 6 different types of camera settings to choose from:

- Static/Static: Both, camera position and rotation, are fixed and do not change
- Static/LookAtCharacter: Camera position stays, but the camera always rotates towards the character position
- Follow/Static: The camera follows the character's position but its rotation is fixed
- Follow/Top-Down: The camera follows the character's position from a top-down perspective
- NearestWorldAxis/Static: The camera always positions itself along the global world axis that is nearest to the character, looking towards the world center/origin
- NearestWorldAxis/LookAtCharacter: Same as above, but the camera always rotates towards the character

I recommend checking out the corresponding demo scenes to get a feeling for them and possible use cases.
