# Project Setup

The following steps describe the needed project settings for using my asset scripts with default values.

## Creating required layers

Navigate to Edit > Project Settings > Tags and Layers and add the following layers (preferably at the written position so that they are correctly to the provided prefabs):

1. "Character" (layer 3)
1. "Ground" (layer 6)
1. "Climbable" (layer 7)

## Creating the "Terrain" and "Player" tag

Navigate to Edit > Project Settings > Tags and Layers and add the following tags to the list:

1. "Player": By default used by the ViewFrustum component to ignore any player object inside the view, e.g. for zooming in the camera or fading the object out.
1. "Terrain": By default used by the LookUpBehavior component to trigger a camera look up when colliding with a tagged object.
