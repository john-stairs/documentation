# Useful resources

As this asset is using Unity's Nav Mesh Agent for commanding selected game objects, I highly recommend reading through the corresponding documentation: [Navigation System in Unity](https://docs.unity3d.com/550/Documentation/Manual/nav-NavigationSystem.html).

The demo uses a URP Decal Projector for the Selection Circle prefab. To prevent other objects, like the units, from being targeted by the projector, Rendering Layers are used:

- [Decal Rendering Feature](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/renderer-feature-decal.html)
- [Rendering Layers](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/features/rendering-layers.html)
