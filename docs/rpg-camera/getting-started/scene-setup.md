# Scene Setup

In the following, you find the steps for correctly setting up your scene with my asset in it.

## Attaching the scripts

All scripts which are related to the character can be found inside Scripts > Character. Copy one of the provided character prefabs or attach the scripts of your choice to your character game object, usually its root:

1. **RPGCamera:** This script contains all general camera functionality like yaw, pitch or zoom. Additional functionality is based on the subcomponents you add to the game object – either manually or by adding a default via button (see screenshot below).
1. **RPGController:** This script uses device input to control the RPGCamera. Without this script, the camera will not move. 
1. **PlayerInput:** This component is automatically added with the RPGController. Open it and assign the RPGInputActions inside folder Input to the "Actions" property. Optionally, set the Behavior to "Invoke C Sharp Events".
1. (Optional) **CursorHandler:** This script is used by the RPGController to control cursor behavior. Add it if you need some cursor handling on top of camera functionality, e.g. hiding and letting it stay in place when camera orbiting starts.
1. (Optional) **RPGMotorExample:** Example character motor implementation based on [Unity's Character Controller documentation](https://docs.unity3d.com/ScriptReference/CharacterController.Move.html). Used as a proof of concept for working camera and character interaction.

<div style="text-align:center">
    <img src="../img/add-default-button.png"/><br>
    Note that not every subcomponent is required for the camera to work!
</div>

## Assigning the right layers

Some of the provided camera subcomponents work with layer masks to filter processed game objects. There are explanation tooltips for each variable that are displayed when hovering over a variable label. Nevertheless, a short example does not harm:

<div style="text-align:center"><img src="../img/layer-mask-example.png"/></div>
 
The View Frustum describes what is in view between the camera and the camera pivot (defined by the Pivot subcomponent). With the setup above, only game objects inside layers "Default" and "TransparentFX" are recognized. However, game objects inside these layers with tag "Player" are ignored.

The Occlusion Handler describes how game objects inside the View Frustum are processed, i.e. if they force the camera to zoom in or if they should be faded out. Objects that are considered by the View Frustum but do not fulfill any of the conditions are not causing anything.

In combination, character game objects with layer "Default" and tag "Player" (like set up in the Character prefabs) do not cause a zoom in, even though the layer "Default" is configured as a zoom condition.

## Using the correct shader (optional)

To make the fading of game objects work, they need to have a material with a Transparent shader assigned, e.g. Unity's "Universal Render Pipeline/Lit" shader. Just check out which shaders are used in the provided demo scenes. 

If the shader does not have ZWrite enabled by default (like the one mentioned above), it will be enabled when the material enters the view frustum and should be faded. However, for complex objects, ZWrite needs to be enabled on game start to be displayed properly. To accomplish this, you can assign the provided EnableMaterialZWrite script to the game object (see the "House" demo prefab as an example).
   
<div style="text-align:center">
    <img src="../img/zwrite-example-left.png" width="50%"/><img src="../img/zwrite-example-right.png" width="50%"/><br>
    Left: ZWrite disabled | Right: ZWrite enabled.
</div>

## Underwater effects (optional)

For leveraging the provided UnderwaterHandler script, two things are required for properly defining a water game object:

1. It must have the "Water" script attached
1. It must have a box collider attached that acts as a trigger

Check out the prefab "Water" in folder Prefabs for reference. 
