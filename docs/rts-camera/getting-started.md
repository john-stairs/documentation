# Getting Started

This chapter covers everything you need to do to fully integrate this asset into your own project.

!!! info
    Note that this asset was developed with Unity's Universal Render Pipeline (URP). Therefore, all provided material is based on URP. However, other render pipelines are also supported by this asset.

## Your own scene

Just drop the Camera Pivot from the prefabs folder into your scene and you are ready to go. Alternatively, you can assign the corresponding scripts of it manually. They can be found inside the Scripts folder:

- RTS Camera
- Subcomponents > Pivot
- RTS Controller (for controlling the RTS Camera)
- Cursor Handler

The RTS Controller will automatically add Unity's "Player Input" component which you need to assign the RTSInputActions from the Input folder to.

## The demo scene

There are two things to make the demo scene working:

1.	Setting up a "Terrain" Layer
1.	Configuring the Decal Renderer Feature

There are two components that use layer masks: The RTS Controller and the Pivot (RPG Camera subcomponent). If you set up User Layer 6 to be "Terrain", prefabs and game objects in the scene should automatically be assigned this layer. If you pick another User Layer, assign the "Terrain" layer to the Terrain object in the scene and configure the Terrain Layers of the RTS Controller and Pivot components of the Camera Pivot game object accordingly.

Click on the Selection Circle in the scene view. The "URP Decal Projector" should give a warning about the missing Decal Renderer Feature. Click the "Open" button, navigate to the bottom of the newly opened window and click Add Render Feature > Decal. Enable "Use Rendering Layers". The selection circle texture should now be visible in the scene.
