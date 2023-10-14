---
description: using unmodded Ryujinx and FileStub
---

# Switch ROM Corruptions

This guide explains how to get Nintendo Switch corruptions working using FileStub and Ryujinx the Nintendo Switch emulator. This method allows for Switch corruptions, but ultimately it is a slow and tedious process due to the lack of savestates.

**This guide presupposes that the game is already operational on the emulator.**\
**If you haven't gotten your game to run in Ryujinx, stop reading this guide and figure this one out.**

_This guide will not show you how to setup the firmware and your prod.keys._\


## Preparing the Corrupt mod

In the main Ryujinx menu, right-click on your game and select Open Mods Directory.

_If you have been opening your games using "File -> Load application from file" and your game doesn't appear in the main screen, you need to go in the Ryujinx settings and setup the Game Directories to where your game file is._

In this directory, you will create a folder called "Corrupt". Inside the Corrupt folder, you will create a folder called "exefs". It is very important that this one is written in lower case.

Go back to the main screen in Ryujinx and right-click on your game and select Extract Data -­> ExeFS. Make it extract  the data in the "exefs" folder you just created.

You should now have a "main" file in the "exefs" folder alongside a few other files.\


## Preparing the main file

Get the "nsnsotool" program from Github at [https://github.com/0CBH0/nsnsotool](https://github.com/0CBH0/nsnsotool)\
Put the tool in the "exefs" folder and open a command prompt to the "exefs" folder.

Run the following command:&#x20;

> nsnsotool.exe main main.decompressed

This will create a decompressed executable. Delete the "main" file and rename the .decompressed one to "main".

## **Preparing the File Corruptor**

The new bigger uncompressed "main" file in that "exefs" folder is the rom that you will corrupt.\
Open FileStub and load that "main" file as your target for RTC.

You will want to use the Vector Engine and realistically only the Classic vector lists.

If you haven't done it already, go to RTC Settings and Uncap the intensity. You'll need massive blasts for the Switch executables.\


## **Finding the alignment**

Nintendo Switch executables are rarely aligned on the 32-bit grid. In most cases, you will need to set your Alignment to "1" for them. If you want to be 100% sure of the alignment needed for your game, you can do the following to test it.

* Set your alignment to 0
* Set your Vector Engine to One/Two
* Open the Glitch Harvester
* Blast at maximum intensity
* Note how big is the generated BlastLayer
* Repeat for Alignment 1,2,3

After having probed all 4 alignments (0,1,2,3), you'll know which one is the right one from which BlastLayer had the most units.

## Blast away

You should now have a setup ready for Switch Corruptions. When you blast using the Glitch Harvester, it will alter the "main" file. To get the results, you have to stop the emulated game and restart it. Because of this, sanitizing is an extremely slow process and is not recommended.

Play around with the Classic Vector lists and you'll find effects. Go ham.

\
