# How To Read
Tips are slip up into sections that are concerning a specific feature set or technical area. 

Tips that require context or extensive work to implement are split up into "Overview", "When To Use", and "Additional Resources" subsections. 


# New Input System
The input system that Unity uses by default as of Unity Version 6000.3

The only Input system is soon becoming deprecated due to this move.

### Using OnMouse Functions
The OnMouse functions that derive from Monobehaviour are part of the old input system and thus require it being reenabled in settings. Unity is working on bringing these functions back in the New Input System.

Ensure that when using the OnMouse functions that both input systems (old and new) are enabled in the project. Required for 6.000 and up.

### Getting Actions
Actions are things like, "Jump", "Attack", "Move" which derive there inputs from one or more devices. This separation of direct device access and input is the key for the New Input System.

You use the default action map by accesing the `InputSystem.actions` array. You can then use the `FindAction(string actionName)` function or index notation `["Action name"]`.

### Triggering On Button Held

The action (or binding) must have the 'Hold' interaction.

### Accessing Device Input Directly
If you want to access input directly from a device and circumvent the Input System's actions array(which can be helpful for fast iteration) you can access devices using the following.
`Device.current.input.()`

<b>Examples</b>

`Mouse.current.position.ReadValue()`

`Keyboard.current.dKey.WasPressedThisFrame()`


### Mouse To World Point (2D)

`Camera.main.ScreenToWorldPoint(Mouse.current.position.ReadValue());`
Although its not recommended to use `Camera.main` because its slow, it's included so that it can work out of the box.

# Performance

### Be careful with GameObject.SetActive()
This function, although not in it of itself expensive to call, can cause lag spikes as the Awake and OnEnable functions for all components on the object and in the children will be called. \
An example of this is when enabling a gameobject that has a TextMeshProUGUI component. Enabling this is expensive because it has to calculate how the text will be formatted and displayed. (Although you might not notice on your gaming pc, I noticed it very clearly on my laptop...)

# Iteration Speed

## Engine Optimizations

### Assembly Definitions

<b>Overview</b>

Assembly Definitions are similar to c# [namespaces](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/namespaces), although they do not replace them, however they come with the added benefit of reducing compile times during code changes and when entering playmode.

Exact performance increase depends a lot on how well it is implemented and how big the project is.

<b>When To Use</b>

It is often good to implement, or at least consider, this as early into the project as possible as it <b>forces</b> you to decouple depencies in order to recieve meaning benefits, or even compile correctly.

If the scope of your project is small or you are in a time crunch(like during a game jam) this isnt as essential as it would be if the project was larger. However it depends on circumstance, if you or your team are on laptops then having reduced compiles times will be much more noticeable even if the project is short lived.


<b>Additional Resources</b>

Quick 7 minute overview
[Assembly Definitions in Unity - Youtube](https://youtu.be/HYqOSkHI674?si=qlnrqraaUjPRq_CL)

In depth explanation of setup
[Speed Up Compile Times in Unity with Assembly Definitions - Youtube](https://youtu.be/eovjb5xn8y0?si=aAo6SPCXMK4pMmbq)

In depth explanation of architecture considerations
[Unity Assembly Definitions Explained (Architecture, Not Just Compile Times) - Youtube](https://youtu.be/OqKEaiQrDHY?si=cZGPBvbdXnF0v_GY)




## Being Designer Friendly
This section is all about creating editor tools that are accesible to designers in order to drive iteration and testing. One of the best resources for this topic is the official [foundations.unity.com](https://www.foundations.unity.com/) site.


