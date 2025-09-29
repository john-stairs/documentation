# RPG View Frustum

## Frustum Shape and Rays per Edge

Since v5.1, there is the possibility to change the shape of the view frustum, i.e. to influence the area which is tested for camera occlusion. While the cuboid shape checks for a consistent frustum plane from pivot to camera, the pyramid shape (default) has only a single frustum plane at the camera, forming a pyramid with its peak at the pivot. You can also see the difference in play mode if you have Gizmos turned on.

The pyramid shape is more forgiving but less performant (additionally influenced by the number of cast rays). Example: If you closely move the character around a pillar object, the cuboid frustum would cause a zoom into first person, whereas the pyramid frustum would not do anything. 

## Occluding Layers and Tags/Layers/Component For Fade Out

The occluding layers determine which game objects in the scene are processed by the camera view frustum. By default, every game object which has one of these layers assigned causes an automatic camera zoom in when it occludes the view to the character.

Objects which should be faded out in this case instead of causing a zoom in can either be tagged with one of the "Tags For Fading" or assigned to a layer of layer mask "Layers For Fading". From v5.3 on, you can also choose the provided script/component "FadeOut" as a criterion for fading objects.

<div style="text-align:center"><img src="../img/occlusion-handling.jpg"/></div>

## Tags/Layers/Component Causing Look Up

Game objects in the scene which are tagged with this tag (or assigned to this layer mask) are triggering the camera look up feature whenever the camera starts lying on them.

## Fade Out Alpha

The alpha to which objects fade out when they enter the view frustum.

## Fade In Alpha

The alpha to which objects fade back in after they left the view frustum.