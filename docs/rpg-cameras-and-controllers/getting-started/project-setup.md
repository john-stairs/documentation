# Project Setup

The following steps describe the needed project settings for using my asset and running the provided demo scenes.

## Installing and activating Unity's Input System

Find the asset in Unity's Package Manager (Window > Package Manager) and press "Import". A warning pops up stating that the asset has Package Manager dependencies. Press "Install/Upgrade" to install missing dependencies, including Unity's Input System. If you have not had the latter in your project activated already, another warning will show up asking you to activate it. If you are planning to only use the new input system, you can click "Yes". Otherwise, I would recommend clicking "No", going to the Edit > Project Settings > Player > Active Input Handling and selecting "Both" from the drop-down list. This way, both input systems can be used in your project. Now you can restart the Unity Editor so that the changes take effect.

!!! note
    This step is required even if you want to stick to Unity's legacy input system. In this case, you would enable "Use Legacy Input System" on each of my input handling scripts, i.e. the RPG Controller and RPG Camera. Moreover, there is an Input Manager provided in Scripts > Inputs > Legacy (will overwrite current inputs on import).

## Creating the "Player" layer

Navigate to Edit > Project Settings > Tags and Layers and add layer "Player" to the list (preferably as "User Layer 8" so that they are automatically assigned to the provided prefabs).

## Creating the "Terrain" tag

Navigate to Edit > Project Settings > Tags and Layers and add tag "Terrain" to the list. This tag is used by default by the RPGViewFrustum script to trigger a camera look up when colliding with a tagged object.

## Creating the needed inputs (required if you want to use the legacy input system)

Navigate to Edit > Project Settings > Input Manager > Select Preset (middle button at the top right) and select "RPGInputManager". Note that this will overwrite any existing adjustments to the currently set up input manager!