# Unity-Quick-Tips

# Using OnMouse Functions

Ensure that when using the OnMouse functions that both input systems (old and new) are enabled in the project. Required for 6.000 and up.

# New Input System

## Getting actions

You use the default action map by accesing the `InputSystem.actions` array. You can then use the `FindAction(string actionName)` function or index notation `["Action name"]` 

## Triggering On Button Held

The action (or binding) must have the Hold interaction.

# Mouse To World Point (2D)

Although its not recommended to use `Camera.main` because its slow, it's included so that it can work out of the box.
`Camera.main.ScreenToWorldPoint(Mouse.current.position.ReadValue());`