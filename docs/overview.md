# Overview

Here is a short overview of the Unity assets documented on this website and what they represent:

- [RPG Camera Lite](./rpg-camera/introduction.md): Basically the vanilla World of Warcraft camera controller without character fade-out and camera look-up when touching the ground.
- [RPG Camera](./rpg-camera/introduction.md): Vanilla World of Warcraft camera controller + fading of objects which are in the way + intelligent pivot positioning ([details](./rpg-camera/introduction.md#variables)).
- [RPG Character Controllers](./rpg-character-controllers/introduction.md): RPG character controllers inspired by famous MMO or Action RPGs, fully contains and integrates the RPG Camera.
- [RTS Camera](./rts-camera/introduction.md): The vanilla Warcraft III camera controller.
- [Planet Platformer Controller](./planet-platformer-controller/introduction.md): Replica of the character controller of Super Mario Galaxy.

## Relation between my RPG assets

The relation between my 3 RPG assets can be easily described when looking into their provided features. From left to right, each asset has a subset of features of the next asset:

<div style="text-align:center">RPG Camera Lite &sub; RPG Camera &sub; RPG Character Controllers</div>

- RPG Camera Lite: Modular RPG camera asset with basic features.
- RPG Camera: Contains all features a modern RPG Camera needs.
- RPG Character Controller: Adds RPG character movement on top of the RPG camera.

Assets can be easily upgraded to the next tier because they are built on the same architecture. A detailed comparison of supported features can be found in the [feature matrix](./feature-matrix.md).
