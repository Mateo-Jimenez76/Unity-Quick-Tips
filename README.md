# Using OnMouse Functions

Ensure that when using the OnMouse functions that both input systems (old and new) are enabled in the project. Required for 6.000 and up.

# New Input System

### Getting actions

You use the default action map by accesing the `InputSystem.actions` array. You can then use the `FindAction(string actionName)` function or index notation `["Action name"]` 

### Triggering On Button Held

The action (or binding) must have the Hold interaction.

# Mouse To World Point (2D)

`Camera.main.ScreenToWorldPoint(Mouse.current.position.ReadValue());`
Although its not recommended to use `Camera.main` because its slow, it's included so that it can work out of the box.

# Performance

### GameObject.SetActive(bool)
This function, although not in it of itself expensive to call, can cause lag spikes as the Awake and OnEnable functions for all components on the object
and in the children will be called. \
An example of this is when enabling a gameobject that has a TextMeshProUGUI component. Enabling this is expensive because it has to calculate how the text will be formatted and displayed. (Although you might not notice on your gaming pc, I noticed it very clearly on my laptop...)
