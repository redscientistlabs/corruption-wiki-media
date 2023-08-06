---
description: Getting Started Corrupting with Simple Mode
---

# Simple Mode

written by Melody

## Introduction with Simple Mode

Ready to start corrupting? RTC provides an incredible, overwhelming amount of tools to work with. This can be nice, but as a beginner it can be easier to learn with some of the more advanced options out of the way. This is where Simple Mode comes in handy. If you are just beginning to learn, you should start by mastering the tools provided here in Simple Mode, and **ensuring you have a firm understanding of what is occuring behind-the-scenes in your corruption.** This is vital when learning to corrupt; take the time to understand your corruptions.

![](<../../.gitbook/assets/image (42).png>)

## Let's Begin

Start by loading up the RTC, launching either BizHawk or Dolphin, and clicking the wizard icon to the left that says, _"Easy Start."_ Next, click, _"Switch to Simple Mode."_ At the top you'll see a prompt asking if you're corrupting 2D or 3D games. For this, we'll assume we're corrupting a 2D game today, so we'll select, _"Classic Platforms."_ If you are corrupting a console such as the GCN or PS2, you'll want to try, _"Modern Platforms."_

![](<../../.gitbook/assets/image (29).png>)

Next, go ahead and load up your ROM into your emulator.&#x20;

{% hint style="info" %}
If you are using RTC with the Bizhawk Emulator, make sure your Rewind and Fast Forward hotkeys are bound properly. Rewind is very useful for reversing back corruption, especially when doing real-time corruption such as manual blasts and auto-corrupt.
{% endhint %}



You'll want to find a spot in your game you think could corrupt well. Perhaps there are certain sprites on screen, or models doing animations, the choice is yours, just find somewhere to save. When you've found this location, press the button, _"Create and select a Glitch Harvester savestate"_

![](<../../.gitbook/assets/image (36).png>)

## What is the Glitch Harvester and Why am I using it?

Corruptions can be implemented real-time and non real-time. The Glitch Harvester is a tool that lets us not only create savestates, but it also lets us save corruptions we've found. After we save these corruptions, not only can we replay them but we can fine-tune them, and we can try to find different results with them. The _"Simple Glitch Harvester"_ provided in the _"Simple Mode"_ part of RTC is a very simplified version of the actual _"Glitch Harvester"_

## Time to Corrupt!

We should have either the Nightmare engine or the Vector engine loaded up, and you can confirm this by looking under the box in the center of the screen that says, _"Engine Parameters."_ The benefit of Simple Mode here is we don't have to provide most of the parameters ourselves, we can simply jump right into corrupting.&#x20;

![](<../../.gitbook/assets/image (45) (1).png>)

Beneath the previously-mentioned box is another box, labelled, _"Real-Time Corruption."_ This is where you'll input your one and only parameter, which is _"Intensity."_ Move the slider up a bit; how much is entirely specific on which game you're corrupting and which engine you are using.&#x20;

![](<../../.gitbook/assets/image (41).png>)

Press the red button labelled, _"Load and Corrupt."_ This is essentially your start button, it loads the savestate and applys the corruption.

![](<../../.gitbook/assets/image (30) (1).png>)

There are two easy ways to figure out what _Intensity_ you should be using. Either we begin with a very high _Intensity_ and work our way backwards, or we begin with a very small _Intensity_ and work our way forwards. I recommend the prior, as doing the latter usually results in a lot of wiggling back and forth at the end. The main goal here is to find an _Intensity_ that manages to hit a lot of _stable addresses_. Hopefully those _addresses_ we hit cause the types of effects we are looking for, and not the types of effects we don't want. Try to find a balance between silliness and unstability.

{% hint style="info" %}
Keep in mind that these corruptions are randomly generated and that the results you are getting are all luck-based.
{% endhint %}

For _real-time_ corruptions, we can use the button, _"Manual Blast."_ This fires a single blast of corruptions at a time, in real-time. That is, we can continue to corrupt further after hitting, _"Load and Corrupt"_ from the _"Glitch Harvester."_ Another handy tool is the, _"Auto-Corrupt"_ button. Here you can continuously blast the game with corruptions.

{% hint style="info" %}
With either of these tools _(Manual Blast and Auto-Corrupt)_ you're likely going to want to lower your intensity, especially if you plan on doing a large number of blasts.
{% endhint %}

## Where do I go from here?

_"Shuffle Algorithm"_ lets you try out different engines. Check the _Basic Guide_ for a more thorough run-down on what each of these engines do. Try shuffling the engine a few times.&#x20;

![](<../../.gitbook/assets/image (15) (1).png>)

An unique feature to the Real-Time Corruptor next to its ability to corrupt in real-time is its ability to also uncorrupt in real-time, sorta. Whenever a corruption is created using the "_Glitch Harvester_", it is possible to attempt to disable it while the game is still running. You can play around with this feature using the button "_BlastLayer : ON/OFF_"

![](<../../.gitbook/assets/image (4) (1).png>)

When you're ready to start learning the rest of the program, simply click, _"Switch to Normal Mode."_ Here you can start making changes to the rest of the parameters each engine uses. Each engine has it's own way of working, so check each section of the _Basic Guide_ respectively. You can freely switch back and forth between normal mode and simple mode if you so desire, so as to access the rest of the parameters.

![](<../../.gitbook/assets/image (50).png>)

## The Next Parameter

Now that you've mastered the use of the _Intensity_ parameter and you've seen _"Auto-Corrupt"_, it only makes sense the next parameter we use is _"Error Delay"_. This provides spacing in-between blasts when we're using the _"Auto-Corrupt"_ function. Try mixing and matching different configurations between the two parameters and seeing how they interact in the overall use of the program. Crashes are very likely so don't be surprised, but it's a learning experience after all. For more information on _"Error Delay"_, again check the _Basic Guide_.

![](<../../.gitbook/assets/image (23) (1).png>)

## The Engines

Here's a quick run-down of some of the easier things you can do with each engine. I recommend you shuffle the engine, then switch to normal view to change the parameters of these engines, then switch back. At first you should only be messing with a few parameters at a time.

![](<../../.gitbook/assets/image (38) (1).png>)

### Nightmare Engine

Changes Bytes in Memory once, either replacing or incrementing/decrementing them. Try switching the _Blast Type_ to either replace, replace or modify, or solely modify.

### Hellgenie Engine

This engine freezes a Unit's value, **which is randomly generated.** _Max Infinite Units_ is what you'll want to play with here. This parameter limits how many changes can be made, which can limit the corruption in the same way a low intensity would. If you aren't getting any effects even with a high intensity, chances are your _Max Infinite Units_ is too low.

### Freeze Engine

Similar to the Hellgenie engine, here we are freezing values, but this time we're **freezing them in place.** For this engine to be effective we need to target values that are supposed to be changing. In both the Freeze and the Hellgenie engine it is likely you'll want to have _"Clear Units on Rewind"_ enabled. This is so that when you load a savestate using the _Glitch Harvester_, old corruptions don't linger. You may want to disable it if you are using BizHawk's rewind function however.

### Distortion Engine

Using the Distortion engine we can backup a copy of some data, and then restore that data back to where it came from at some point in the future. This is accomplised through, _"Distortion Delay"_ which is a measurement of _\*Steps_ into the future. It's roughly similar to frames, but not the same thing.

### Pipe Engine

**Pipes** are bindings of one address to another. This results in data being, _"bled"_ from one location to another, and can result even in data going between memory domains. _"Max Infinite Units"_ again is our control parameter. This engine can be hard to utilize successfully at first, and is best used with _Virtual Memory Domains_ and an otherwise thorough understanding of how your game handles it's memory.

### Vector Engine

This engine is great for messing with modern 3D games. Simply provide it a _Limiter List_ and a _Value List_. When the corruptor selects data to corrupt, it gets checked against the _Limiter List_. You could think of it similar to checking the value's data type. Is it positive, negative, whole, one or zero? If the value we're checking to corrupt doesn't match up with the _Limiter List_, it's not going to be part of the corruption. The _Value List_ is what we're replacing the data with.

### Custom Engine

You can also modify these engines and blend them together using the _Custom Engine_, but it's outside the scope of this article. Still worth reading however, see, _Basic Guide_.

### Blast Generator

This engine is able generate algorithmic blasts that are not real-time. It works similarly to older corruptors like the Vinesauce Rom Corruptor but allows for a deeper and more granular control of the generation algorithm.

## Finally

I hope this guide has helped you get started in making your first corruptions. It's a continuous learning experience, remember to always try new things and don't be scared to ask questions in the help channel of the RTC Discord.
