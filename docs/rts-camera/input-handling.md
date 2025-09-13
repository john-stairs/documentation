# Input handling

This section gives an overview and some details about the input actions that are provided via Input > RTSInputActions.

- **Cursor Position:** Current cursor position in screen coordinates. Used for triggering camera movement whenever the cursor is close to the screen boundaries. When using the "Gamepad" control scheme, the cursor is locked in the screen center to allow easier unit selection.
- **Camera Movement:** "Non-cursor" camera movement, e.g. via WASD.
- **Yaw Amount:** Horizontal camera rotation
- **Yaw Amount With Modifier:** Horizontal camera rotation only if a modifier is additionally pressed. For example, the middle mouse button needs to be pressed to enable yawing via mouse movement.
- **Pitch Amount:** Vertical camera rotation.
- **Zoom Amount:** Increasing/decreasing the camera distance to the pivot.
- **Select:** Selects the clicked unit if it has a Selectable Layer.
- **Command:** Command the selected object to move to the clicked location (must have a Terrain Layer)
- **Jump To Selection:** Let the camera immediately jump to the currently selected object.
- **Reset View:** Resets the camera parameters to their start values.
