# Frequently asked questions

<!-- 
!!! info
    Questions about the RPG Camera can be found [here](../rpg-camera/faq.md).
-->

## Why do I get so many errors?

The reason could be a wrong setup. Please set up everything according to the manual. Use the demo scene to verify that everything is set up correctly.

## Why do I get error CS0246: "The type or namespace name 'InputAction' could not be found"?

You have forgot to install/activate Unity's new Input System. Download it via the Package Manager and enable it in the Project Settings under "Player".

## Can I use a gamepad with your asset?

Yes, this asset uses Unity's Input System – just rebind the RPGInputActions to your needs. If you want to stick with the old Input Manager, this is supported as well (do not forget to check "Use Legacy Input System" on my scripts).

## Can I use the camera and character controller scripts separately?

Yes, just make sure that you set up the individual component according to [Scene Setup](./getting-started/scene-setup.md).

## How can I use my own camera object and not the main camera?

Set RPGCamera script variable "UsedCamera" to "Assigned Camera" and assign the camera game object you want to use to variable "CameraToUse". Alternatively, if you want to automatically spawn a new camera, select "Spawn Own Camera" as "UsedCamera".

## Why does my character look like it is falling all the time after the initial setup?

This is usually due to a wrong character object setup. Please check the following:

1. Assign the character game object to a layer which is part of the "Ignored Layers" of the RPGMotor. The recommendation is to assign it and all of its children to the "Player" layer and have this layer set as one of the "Ignored Layers"
1. Play around a bit with the "Grounded Tolerance" variable of the RPGMotor. If gizmos are enabled, you can see how the variable influences the sphere which is used for the grounded check. While in play mode, it is colored green if ground was detected, otherwise red
1. Make sure that the root object is not scaled. If it is, please set its scale to Vector3.one (1,1,1) and scale the model and the Character Controller component collider separately

## Where are the animator parameters set?

You can find the communication between script and Mecanim in method `SetValuesInAnimator` of the RPGMotor.

## Which animations from Mixamo did you use in the demo?

Please check the section [Adding animations](./getting-started/scene-setup.md#adding-animations) of the Scene Setup page for details and the corresponding download links.

## Why is my character falling through moving objects?

Each moving object you want your character to walk on needs a kinematic rigidbody component attached.

## Why doesn't my character stay on moving platforms?

The moving platform has to have at least the MovingPlatform script and a box trigger collider assigned (used for detecting passengers). I recommend checking out the provided "Moving Platform" prefabs which are also used in the demo scenes.

## Why does swimming not work?

For leveraging the swimming feature of the RPGMotor, three things have to be considered:

1. You need a water game object which has the "Water" script/component assigned
1. This water game object must have a box collider that acts as a trigger attached
1. The variable "Swimming Start Height" of the RPGMotor controls at which local height the character should start to swim (visualized by a small blue plane when gizmos are enabled)

Check out the prefab "Water" in folder Prefabs for reference.

## Why are objects between camera and pivot not faded out?

It is very likely that mentioned objects have no transparent/fade shader assigned to their material and/or a layer which is not one of the "Occluding Layers" set in the RPGViewFrustum.