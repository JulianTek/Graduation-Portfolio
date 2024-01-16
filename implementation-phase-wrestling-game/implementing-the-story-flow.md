# Implementing the story flow

## What is the problem?

I want to create a foundation that I can use throughout the game. This mainly includes a system for making choices

## How did I solve this?

### <mark style="color:blue;">Requirement prioritization (Workshop)</mark>

I need to know what's most important for developing the game. This will give an overview of what I will focus on

The focus priorities are

1. The dialogue/Choice system. This will be the main gameplay mechanic, and will therefore be incredibly important
2. &#x20;The story. This is how we disguise the choices from goal to gameplay
3. The visuals. These are not as important

### <mark style="color:blue;">Prototyping (Workshop)</mark>

I use [NodeCanvas](https://nodecanvas.paradoxnotion.com), a tool for creating dialogue trees, AI Behaviour trees, and AI State machines, to not only create the dialogue but also to direct the cutscenes. This is how I do it

#### Cinemachine

Cinemachine is a tool that expands on the Unity camera. These can be used to dynamically move cameras based on a GameObject's position.

#### Code

I have several methods that can be called from NodeCanvas. They are the following:

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

This method aims the camera at a specific target.

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

This method enables or disables an object.

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

These 2 handle moving characters. The first one uses a NavMesh agent. This is to be used when wanting to visually move a character, like in a cutscene

The second method is to be used when you want to move the character without any restrictions from the NavMesh, or move a character immediately.

I disable the NavMesh agent because if I do not, the program will still try to use the NavMesh to move, and will throw an exception if this is not possible

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

This function rotates a character. I use EulerAngles so someone may be able to use the Unity Editor to check where an object goes and then copy the values.

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

My animation controllers use booleans to switch between animations, this is how I animate characters.

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

This swaps between two cameras, eg. when I need to have a third person camera enabled and disable the camera that is active during cutscenes

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

There are sections where the player can move. This disables and enables input if need be.

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

This code switches cameras and disables or enables input if need be. This is used when entering or entering a cutscene. This method is usually used at the beginning (and the end) of a dialogue tree.

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

This sets all animation parameters back to false, resetting the animation back to the idle animation

## What is the result?

These functions are what allows the story to be choreographed. Below is one of the choices you can make in the game, to illustrate this point

{% file src="../.gitbook/assets/Unity_oui827yU91.mp4" %}
