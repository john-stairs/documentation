# Frequently asked questions

## Why do I get so many errors?

The reason could be a wrong setup. Please set up everything according to the manual. Use the demo scene to verify that everything is set up correctly.

## Can I use a gamepad with your asset?

Yes, this asset uses Unity's Input System – just rebind the RPGInputActions to your needs.

## How can I use my own camera object and not the main camera?

Set RPGCamera script variable "UsedCamera" to the camera object which should be controlled.

## Why are objects between camera and pivot not faded out?

It is very likely that mentioned objects have no transparent/fade shader assigned to their material and/or a layer which is not one of the "Occluding Layers" set in the RPGViewFrustum.
