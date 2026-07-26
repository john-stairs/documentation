# Frequently asked questions

!!! info
    Questions about the embedded RPG Camera can be found [here](../rpg-camera/faq.md).

## Why do I get so many errors?

The reason could be a wrong setup. Please set up everything according to the manual. Use the demo scene to verify that everything is set up correctly.

## Can I use a gamepad with your asset?

Yes, this asset uses Unity's Input System – just rebind the RPGInputActions to your needs.

## Can I use the camera and character controller scripts separately?

Yes, just make sure that you set up the individual component according to [Scene Setup](./getting-started/scene-setup.md).

## Why does my character look like it is falling all the time after the initial setup?

This is usually due to a wrong character object setup. Please check the following:

1. Assign the character game object to a layer which is not one of the "Walkable Layers" of the RPGMotor. The recommendation is to assign it and all of its children to the "Character" layer
1. Play around a bit with the `Grounded Tolerance` variable of the RPGMotor. If gizmos are enabled, you can see how the variable influences the sphere which is used for the grounded check. While in play mode, it is colored green if ground was detected, otherwise red

## Where are the animator parameters set?

The RPGMotor calls the AnimationHandler inside method "Animate". The AnimationHandler then sets the corresponding animator parameters accordingly. 

## Which animations from Mixamo did you use in the demo?

Please check the section [Importing third-party assets](./getting-started/project-setup.md) of the Project Setup page for details and the corresponding download links.

## Why doesn't my character stay on moving platforms?

The moving platform has to have at least the MovingPlatform script and a box trigger collider assigned (used for detecting passengers). I recommend checking out the provided "Moving Platform" prefab which is also used in the demo scene.

## Why does swimming not work?

For leveraging the swimming feature of the RPGMotor, three things have to be considered:

1. You need a water game object which has the "Water" script/component attached
1. This water game object must have a box collider that acts as a trigger attached
1. The variable `Personal Start Level` of the SwimmingHandler controls at which local height the character should start to swim (visualized by a small blue plane when gizmos are enabled)

Check out the prefab "Water" in the prefabs folder for reference.

## Why is my Isometric RPG Character not turning towards the cursor?

The IsoRPGController determines the facing direction based on the `Ground Layers` of the SceneManager which is automatically spawned if there is none in the scene. By default, the `Ground Layers` only consist of layer 6, which corresponds to the `Ground` layer if the [Project Setup](./getting-started/project-setup.md) was followed.