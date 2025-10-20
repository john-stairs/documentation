# Project Setup

The following steps describe the needed project settings for using this asset and running the provided demo scenes.

## Creating the "Ground" layer

Navigate to Edit > Project Settings > Tags and Layers and add layer "Ground" to the list – preferably as "User Layer 8" so that they are automatically assigned to the provided prefabs. Otherwise, you would have to assign the layer manually to all ground objects. You can search for "Ground" in the provided demo scenes to find all relevant game objects.

## Disabling the project's global gravity 

Navigate to the Physics settings of the project (Edit > Project Settings > Physics) and set the global Gravity to `0,0,0`. Otherwise, this will impact the gravity calculations of the asset's physics engine and cause undesired side effects.

Now you are already good to go to run the demo.
