# Project Setup

The following steps describe the needed project settings for using my asset and running the provided demo scenes.

## Installing and activating Unity's Input System

Find the asset in Unity's Package Manager (Window > Package Manager) and press "Import".

!!! info
    This asset is using Unity's Input System. If you are using a version below Unity 6, a warning pops up on import stating that the asset has Package Manager dependencies. Press "Install/Upgrade" to install missing dependencies including Unity's Input System. If you have not had the latter in your project activated already, another warning will show up asking you to activate it.

## Creating the "Player" layer

Navigate to Edit > Project Settings > Tags and Layers and add layer "Player" to the list (preferably as "User Layer 8" so that they are automatically assigned to the provided prefabs).

## Creating the "Terrain" tag (optional)

Navigate to Edit > Project Settings > Tags and Layers and add tag "Terrain" to the list. This tag is used by default by the RPGViewFrustum script to trigger a camera look up when colliding with a tagged object.

## Activating both input system

Navigate to Edit > Project Settings > Player and set the "Active Input Handling" to "Both".

## Using the legacy input system (optional)

Create the needed inputs by navigating to Edit > Project Settings > Input Manager > Select Preset (middle button at the top right) and select "RPGInputManager". 

!!! note
    This will overwrite any existing adjustments to the currently set up input manager!
