# Useful Interfaces

Below you find interfaces that you can implement to create custom components that seamlessly integrate with my asset.

## RPGCamera subcomponents

Every subcomponent of the RPGCamera is based on an interface which can be found in the "Interfaces" subfolder. For a custom subcomponent, implement the corresponding interface and assign it to the game object. Make sure that there is only one component per interface assigned. If the custom subcomponent was found, its entry will be displayed in green at the top of the RPGCamera script.

## ICursorHandler

This interface is used by the RPGController to control cursor behavior and UI consideration. It provides methods to show and hide the cursor, or method "IsCursorOverUI" for checking if the cursor is over an UI element. Check out the provided **CursorHandler** which implements this interface. Depending on the result of "IsCursorOverUI", the RPGController allows or disallows camera control.

## IMotor

Implement this interface if you want to use the RPGController for controlling character movement as well. An example implementation can be found in **RPGMotorExample**. 

Note: It is not required to have a component implementing this interface on the character game object to make the RPGCamera work. However, there are use cases where orchestration between camera and motor is required. Example: The Rotation Sync (character and camera rotating together) cannot work if the rotated degrees of the character is not known.
