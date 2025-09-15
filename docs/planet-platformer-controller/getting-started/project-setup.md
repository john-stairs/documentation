# Project Setup

The following steps describe the needed project settings for using this asset and running the provided demo scenes.

## Installing and activating Unity's Input System

Find the asset in Unity's Package Manager (Window > Package Manager) and press "Import". A warning pops up stating that the asset has Package Manager dependencies. Press "Install/Upgrade" to install missing dependencies, including Unity's Input System. If you have not had the latter in your project activated already, another warning will show up asking you to activate it. Press "Yes" and let the Unity Editor restart. This enables the Input System in your project (under Edit > Project Settings > Player > Active Input Handling). After the restart, you are also prompted with the TextMesh Pro Importer where you can decide if you want to additionally import the TMP Essentials which are used inside the provided UI prefabs and used in the demo.

## Creating the "Ground" layer

Navigate to Edit > Project Settings > Tags and Layers and add layer "Ground" to the list – preferably as "User Layer 8" so that they are automatically assigned to the provided prefabs. Otherwise, you would have to assign the layer manually to all ground objects. You can search for "Ground" in the provided demo scenes to find all relevant game objects.

## Disabling the project's global gravity 

Navigate to the Physics settings of the project (Edit > Project Settings > Physics) and set the global Gravity to `0,0,0`. Otherwise, this will impact the gravity calculations of the asset's physics engine and cause undesired side effects.

Now you are already good to go to run the demo.
