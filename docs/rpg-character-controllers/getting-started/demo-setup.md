# Demo Setup

The following steps describe the needed third-party imports for using my asset and running the provided demo scenes.

## Importing third-party assets (optional)

Steps in this section are optional depending on what you want to reuse for your project or how complete the provided demo scene should be. It will also run without the below third-party assets, but character model and animations would be missing.

[FREE Low Poly Human - RPG Character](https://assetstore.unity.com/packages/3d/characters/humanoids/fantasy/free-low-poly-human-rpg-character-219979) by Blink

After import, 

1. Navigate to Window > Rendering > Render Pipeline Converter
1. Select "Built-in" and "URP (Universal Renderer)" and check "Material Shader Converter"
1. Press "Scan" and "Convert Assets" afterwards

For Character fading to work, navigate to Blink's folder "Materials_Humans" and set the surface type of all contained materials to "Transparent". 

***

[FREE - 32 RPG Animations](https://assetstore.unity.com/packages/3d/animations/free-32-rpg-animations-215058) by Blink

Just import the asset, nothing else to do here.

***

There are 8 animations from Mixamo in the provided animator override I am unfortunately not allowed to ship with my asset. Nevertheless, it is possible to download them for free on their website if you want to use them in your project. Here are the links:

1. [Crouch Idle 01](https://www.mixamo.com/#/?page=1&query=crouch+idle+01&type=Motion%2CMotionPack)
1. [Crouch Walk Forward](https://www.mixamo.com/#/?page=1&query=Crouch+Walk+Forward+&type=Motion%2CMotionPack) -> here the archer animation
1. [Hanging Idle](https://www.mixamo.com/#/?page=1&query=Hanging+Idle&type=Motion%2CMotionPack) (= Climbing Idle)
1. [Hanging Idle (1)](https://www.mixamo.com/#/?page=1&query=Hanging+Idle&type=Motion%2CMotionPack) (= Ledge Grab Idle)
1. [Climbing Up Wall](https://www.mixamo.com/#/?page=1&query=Climbing+Up+Wall&type=Motion%2CMotionPack)
1. [Climbing Down Wall](https://www.mixamo.com/#/?page=1&query=Climbing+Down+Wall&type=Motion%2CMotionPack)
1. [Braced Hang Shimmy](https://www.mixamo.com/#/?page=1&query=Braced+Hang+Shimmy&type=Motion%2CMotionPack) (= Climbing Left/Right)
1. [Left Shimmy](https://www.mixamo.com/#/?page=1&query=Left+Shimmy&type=Motion%2CMotionPack) (= Ledge Grab Strafe Left/Right)

**Crouch Walk Forward** needs to be copied twice, once for crouch-walking left (Root Transform Rotation > Offset: 90) and once for crouch-walking right (Root Transform Rotation > Offset: -90).

**Braced Hang Shimmy** and **Left Shimmy** need to be copied and mirrored via checking the "Mirror" checkbox under the "Animation" tab.

## Importing my asset

Find the asset in Unity's Package Manager (Window > Package Manager) and press "Import". 

!!! note
    Restart Unity now to get all references and animation correctly linked.
