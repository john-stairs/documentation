# Useful Interfaces

Below you find interfaces that you can implement with your own scripts. 

!!! note
    These implementing classes/components have to be assigned to the same object as my RPG camera or motor scripts which should use them.

## IPointerInfo

This interface is used by the RPG Camera. It provides the method `IsPointerOverGUI` for checking if the cursor is over an UI element and – as a result – deactivates all camera input logic. Since this asset does not provide an own UI, feel free to implement this interface in your own code to seamlessly integrate my camera logic. Refer to provided component **RPGPlayerExample** to see an example implementation using the Utils method `IsPointerOverGUI`.

## IPlayer

This interface is mainly used by the RPG Motor. It provides methods such as `CanMove`, `CanRotate` or `CanFly`. As the names suggest, implement these methods for applying movement or rotation impairing effects on the character or enabling/disabling flying or a target lock. Refer to the provided **RPGPlayerExample** script inside the Character folder for an example interface implementation.

## ITransportable

Implement this interface to make an object transportable for the Moving Platform (see the RPGMotor script for an example implementation). 

## IRPGCamera, IRPGViewFrustum, IRPGController, IRPGMotor

For completeness, there are also interfaces provided for each of the character scripts. So feel free to easily replace one of my components by implementing the corresponding interface yourself. 