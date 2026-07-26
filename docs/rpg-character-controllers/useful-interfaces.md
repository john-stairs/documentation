# Useful Interfaces

Below you find a selection of interfaces that you can implement to create custom components that seamlessly integrate with my asset.

!!! info
    Interfaces of the embedded RPG Camera can be found [here](../rpg-camera/useful-interfaces.md).

## RPGMotor subcomponents

Every subcomponent of the RPGMotor is based on an interface which can be found in the Interfaces subfolder. For a custom subcomponent, implement the corresponding interface and assign it to the game object. Make sure that there is only one component per interface assigned. If the custom subcomponent was found, its entry will be displayed in green at the top of the RPGMotor script.

## ICharacter

This interface is mainly used by the RPGController. It provides all kinds of character-related methods for influencing camera and character movement:

- `HasTarget`: Checks whether the character has a target (used for target lock mechanic)
- `GetTargetPosition`: Gets the target's position in world coordinates (used for target lock mechanic)
- `GetMovementSpeedMultiplier`: For apply movement impairing effects
- `IsDead`

## ITransportable

Implement this interface to make an object transportable for the Moving Platform (see the RPGMotor script for an example implementation). 
