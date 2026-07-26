# Frequently asked questions

## Why do I get so many errors?

The reason could be a wrong setup. Please set up everything according to the manual. Use the demo scene to verify that everything is set up correctly.

## Can I use a gamepad with your asset?

Yes, this asset uses Unity's Input System – just rebind the RPGInputActions to your needs.

## How can I use my own camera object and not the main camera?

Assign the camera game object you want to use to RPGCamera variable "Used Camera".

## Why are objects between camera and pivot not faded out?

It is very likely that mentioned objects have 

- no transparent shader assigned to their material
- a layer which is not in the "Checked Layers" of the ViewFrustum
- set up as a Fade Condition in the OcclusionHandler

See [Assigning the right layers](./getting-started/scene-setup.md#assigning-the-right-layers).
