# RPG Builder

[John's RPG Builder Integration](https://johnstairs.com/rpg-character-controllers/integrations/rpg-builder/buy.html) provides a seamless integration to Blink's [RPG Builder](https://github.com/ThomasBlinkStudios/RPG-Builder-Unity-Framework).

## Getting Started

1. Import my asset into your RPG Builder project
1. Pick one of the character prefab and assign it in the RPG Builder editor to a Gender under Character > Races.
1. Uncheck "Dynamic Animator" and Save
1. Set up additional action keys for covering all features under Settings > General > Action Keys > Action Key List:
    1. RotateLeft
    1. RotateRight        
    1. MoveForwardFirstHalf
    1. MoveForwardSecondHalf
    1. Descend
    1. Ascend
    1. ToggleAutorunning
    1. ToggleWalking
    1. ToggleCrouching
1. For mounts, configure the following in the Effect of type "Mount":
    1. Assign a mount prefab that has the provided Mount Animation Handler script assigned (see example prefab "Bear Mount")
    1. For the Animator Controller, use the provided Mount Animator or the example Bear Mount animator override 

## Video

<div style="text-align:center">
    <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/uv4kyggatUI?si=j-f3qifYo1o-sZew" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

## Version history

### v1.0

- First release