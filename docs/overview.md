# Overview

Here is a short overview of the Unity assets documented on this website and what they represent:

- [RPG Camera Lite](./rpg-camera/introduction.md): Basically the vanilla World of Warcraft camera controller without character fade-out and camera look-up when touching the ground.
- [RPG Camera](./rpg-camera/introduction.md): Vanilla World of Warcraft camera controller + fading of objects which are in the way + intelligent pivot positioning ([details](./rpg-camera/introduction.md#variables)).
- [RPG Cameras & Controllers](./rpg-cameras-and-controllers/introduction.md): RPG camera and character controllers inspired by famous MMO or Action RPGs.
- [RTS Camera](./rts-camera/introduction.md): The vanilla Warcraft III camera controller.
- [Planet Platformer Controller](./planet-platformer-controller/introduction.md): Replica of the character controller of Super Mario Galaxy.

## Relation between my RPG assets

The relation between my 3 RPG assets can be easily described when looking into their provided features. From left to right, each asset has a subset of features of the next asset:

<div style="text-align:center">RPG Camera Lite &sub; RPG Camera &sub; RPG Cameras & Controllers</div>

- RPG Camera Lite: Modular RPG camera asset with basic features.
- RPG Camera: Contains all features a modern RPG Camera needs.
- RPG Cameras & Controller: Adds RPG character movement on top of the RPG camera.

Assets can be easily upgraded to the next tier because they are built on the same architecture (wip). A detailed comparison of supported features can be found in the [feature matrix](./feature-matrix.md).

!!! info
    I have started to build my RPG assets from scratch with a new architecture to make maintainability and extensibility much easier by following industry best practices. As a result, the "RPG Camera" and "RPG Cameras & Controllers" assets are currently on different code stacks. You can still upgrade between both of them, but their code base is different. Therefore, the upgrade does not happen seamlessly but rather needs a separate setup.