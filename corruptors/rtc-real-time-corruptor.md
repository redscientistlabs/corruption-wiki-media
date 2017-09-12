# Real-Time Corruptor for BizHawk

###### Author: [Phil Girard](http://redscientist.com/)

###### Source: [https://github.com/ircluzar/RTC3/](https://github.com/ircluzar/RTC3/)

###### Download: [http://redscientist.com/\#/rtc](http://redscientist.com/#/rtc)

The Real-Time Corruptor for BizHawk is a Dynamic Corruptor for emulated games. It's a mod to the Open Source BizHawk Emulator that works by modifying live data from virtual memory chips of emulated systems.

### Index

* [**Index**](#index "Literally this")
  * [**Quick Start**](#quick-start)
  * [**Fundamentals of RTC**](#fundamentals-of-rtc)
  * [**Frequently asked questions**](#frequently-asked-questions)
  * [**Basic**](#basic-guide)
    * [**RTC Vocabulary**](#rtc-vocabulary)
      * [Blast](#blast)
      * [BlastUnit](#blastunit)
      * [BlastLayer](#blastlayer)
      * [StashKey](#stashkey)
      * [Stockpile](#stockpile)
      * [Memory Domain](#memory-domain)
      * [Emulation Step](#emulation-step)
    * [**General Parameters**](#general-parameters)
      * [Auto-Corrupt](#auto-corrupt)
      * [Manual Blast](#manual-blast)
      * [Error Delay](#error-delay)
      * [Intensity](#intensity)
      * [Blast Radius](#blast-radius)
    * [**Memory Domains**](#memory-domains)
    * [**Corruption Engines**](#corruption-engines)
      * [Nightmare Engine](#nightmare-engine)
      * [Hellgenie Engine](#hellgenie-engine)
      * [Distortion Engine](#distortion-engine)
      * [Freeze Engine](#freeze-engine)
      * [Pipe Engine](#pipe-engine)
      * [Vector Engine](#vector-engine)
      * [External ROM Plugin](#external-rom-plugin)
  * [**Advanced**](#advanced-guide)
    * [**Glitch Harvester**](#glitch-harvester)
      * [Action Panel](#action-panel)
      * [Savestate Manager](#savestate-manager)
      * [Intensity](#intensity)
      * [Action Modifiers](#action-modifiers)
      * [Action Triggers](#action-triggers)
      * [BlastLayer Toggle](#blastlayer-toggle)
      * [Reroll Selected](#reroll-selected)
      * [Render Output](#render-output)
      * [Stash History](#stash-history)
      * [Stockpile Manager](#stockpile-manager)
    * [**Stockpile Player**](#stockpile-player)
    * [**RTC Multiplayer**](#rtc-multiplayer)
      * [Connecting RTCs together](#connecting-rtcs-together)
      * [Metagames and Multiplayer Features](#metagames-and-multiplayer-features)
  * [**Expert**](#expert-guide)
    * [**Hotkeys**](#hotkeys)
    * [**Blast Editor \(Editing BlastLayers\)**](#blast-editor)
    * [**Virtual Memory Domains**](#virtual-memory-domains)
      * [Virtual Memory Domain Pool](#virtual-memory-domain-pool)
      * [Virtual Memory Domain Generator](#virtual-memory-domain-generator)
    * [**Generating Active Tables**](#generating-active-tables)

#### Quick Start

The Real Time Corruptor was designed with ease of use in mind, if you want to get right into the action simply load a ROM and click “Easy Start” and you are away! \(_Instant results not always guaranteed\)_

#### Fundamentals of RTC

First, let’s go over the basic fundamentals of how this corruptor functions.

Video game corruption happens when an emulated video game whose program files were altered either in the emulated game’s memory \(RAM\) or in the ROM itself. A real-time corruption is when the corruption itself occurs while the game is running or when the effects can be altered on a time basis.

**RTC **is a mod for BizHawk, which means that any emulated system that BizHawk supports _should_ be compatible. Every system is detailed as a series of memory chips known as Memory Domains. The corruption will be generated for the selected domains in the main window. Certain engines/plugins may ignore the selected domains as part of their design.

What is usually known as an iteration in static corruptors, is called a Blast in the RTC. A blast consists of a series of operations that are to be applied in the data located on the emulated game’s memory banks. \(RAM, VRAM, ROM, etc.\)

**The Auto-Corrupt function **attaches the blast generation to the emulated game’s clock. Smaller blasts on a fast clock will create a constant flow of randomly generated corruption. This flow can be controlled by three parameters: The **Error Delay,** which is a divider linked to the game clock, The **Intensity **which is a multiplier for the number of corruption units to be generated \(which depends on the selected engine\). The **Blast Radius** determines how is the corruption is spread on the selected domains.

#### Frequently asked questions

**What is the difference between Attached Mode and Detached Mode?**

Detached mode is the default mode in RTC 3. It detaches RTC and Bizhawk in two processes and lets them communicate through a homemade system called NetCore. This allows RTC to stay alive if BizHawk crashes and allows for game states to be kept saved outside of BizHawk when using "Game Protection".

RTC Multiplayer is exclusive to Attached Mode since it uses the NetCore to connect two RTCs together. In Attached Mode, you can use the Classic AutoKillswitch by opening it from the Launcher or via the Settings Menu.

Detached Mode has its own embedded AutoKillswitch.

**RTC doesn't start on my computer**

-&gt; Have you tried stock Bizhawk? Do note, that as of Bizhawk 2.0, Bizhawk is 64bit only and supports operating systems Windows 7 and upwards. As of release 3.0, the RTC is based on Bizhawk version 1.11.9 which can be obtained here: [https://github.com/TASVideos/BizHawk/releases/download/1.11.9/BizHawk-1.11.9.1.zip](https://github.com/TASVideos/BizHawk/releases/download/1.11.9/BizHawk-1.11.9.1.zip)

Alternatively, the "Start BizHawk without RTC" option will load BizHawk without the Mod.

-&gt; Have you installed the prereqs? This is essential for BizHawk to run properly. you can grab those from there too: [http://tasvideos.org/BizHawk.html](http://tasvideos.org/BizHawk.html)

-&gt; Make sure your computer is decent. If it's too old then maybe the rendering options of BizHawk may not work. We've seen that problem happen with old Core2Duo chipsets for computers using Internal Graphics.

** Why does RTC wants to be allowed in the Windows Firewall?**

RTC uses networking for a bunch of stuff. Here's more details about those:

-&gt; Loopback UDP: Used for the Auto-KillSwitch and External ROM Plugins

-&gt; Loopback TCP: Used for Detached Mode \(StandaloneRTC communicating with Modded Bizhawk\)

-&gt; TCP: Used for RTC Multiplayer

The features mentioned above WILL NOT WORK if RTC isn't allowed in the firewall.

** Why are certain RTC Cores running slow or RTC running slow in general **

BizHawk is one hell of an emulator. It features a ton of emulator cors and tools to create Tool-Assisted Speedruns. In order for these speedruns to be accurate to the real-life systems they emulate, some of those do extra operations and disable optimizations that might cause faster but inaccurate emulation.

Some emulator cores are faster than others. QuickNes is generally faster than NesHawk for example.

Unfortunately, if the whole thing is still too slow, your only solution might be to upgrade your computer. For comparison, RTC works just fine on a mobile 2nd-Gen Core i3.

**This Emulator core doesn't work with RTC**

This problem usually happens with snes9x. It's not working. The problem is on BizHawk side. One day they'll finish porting it I guess.

**Can RTC work with another emulator than BizHawk?**

The mod could probably be ported, but that would require a ton of modifications, and that's only possible if the other emulator is open source. At this point in time, there's more chances that the Windows Glitch Harvester gets ported for other emulators than RTC, due to a more generic approach in WGH's design.


# Basic Guide

### RTC Vocabulary

##### Blast

A Blast is the action of generating and/or applying a BlastLayer item \(The action of corrupting\). When being generated, a Blast will contain a certain amount of corruption instructions. The amount of generated corruption instructions is defined by the Intensity setting.

RTC is built in a way that corruption is always generated and saved in cache before being applied. This allows replayability, manipulation and real-time interaction. When applied, byte-changing instructions usually backups values before modifying them. This allows corruption to be theorically disabled/reapplied on the fly, although this doesn't always work. Unit types that work by re-executing themselves such as Cheats and Pipes do not take backups. Instead, they simply get removed from their execution pools. This means that while their effect may be stopped in real-time, it also may not be completely reverted.

##### BlastUnit

This represents one Unit of corruption instructions. The inner BlastUnit type depends of the engine that generated it and may contain one or many Adresses, Values and extra parameters.

##### BlastLayer

Type of item that contains corruption instructions generated from a corruption engine.

A BlastLayer is usually encapsulated within a StashKey and can be manipulated using the BlastEditor or by merging multiple BlastLayers in the Glitch Harvester's Stockpile Manager. It can also be appended to another Savestate by using the Inject function of the Glitch Harvester.

BlastLayers that are ran from the Stockpile Player or from the Glitch Harvester can be deactivated and reactivated on the fly \(if applicable\).

##### StashKey

Type of item that contains information about a game, its game state and an attached BlastLayer \(Corruption instructions\).

Corrupting using the Glitch Harvester generates StashKeys in the Stash History. They can later be manipulated and/or added to a Stockpile.

##### Stockpile

Type of item that contains StashKeys. It can be saved as a file that includes Stockpile items, Game Binaries, Savestates, corruption instructions, and information related to BizHawk emulator cores, plugins and config.

Stockpiles can be managed using the Glitch Harvester.

Stockpiles can be replayed using the Stockpile Player.

##### Memory Domain

Item that represents a chip or memory pool on an emulated system. Memory Domains are native to BizHawk but the Memory Domains listed in RTC are proxies to the real Memory Domains. While this fact makes very little difference in terms of how they work, it allows for Virtual Memory Domains to coexist with real ones. Virtual Memory Domains are essentially interfaces to Real Memory Domains with blacklisted adresses.

##### Emulation Step

RTC is hooked to BizHawk's clock using its generic CPU Step loop. This means that RTC's clock is tied to the currently running Emulator Core. The Emulation Step runs in continuous loop and is throttled automatically by BizHawk in order to make the game run at a normal speed. Pausing the emulator in BizHawk causes this loop to also get pause, therefore halting any automatic generation of corruption.

### General Parameters

##### Auto-Corrupt

When this is enabled, RTC attempts to Generate and Execute a BlastLayer on every Emulation Step. The amount of corruption can be set by changing the Intensity and Error Delay settings.

_A Blast happens on every Corrupt Step_

##### Manual Blast

Alternatively to Auto-Corrupt, Blasting a game with corruption can be totally manual.

Blasts with a bigger Intensity can be as effective as a controlled stream of corruption. It does give the user more control on when the game is altered.

##### Error Delay

→Only Applicable to AutoCorrupt

The Error Delay is a divider to the amount of generated corruption. This defines Auto-Corrupt will Blast the game every X steps.

Every Emulator Step that causes Auto-Corrupt to Blast is called a Corrupt Step.

##### Intensity

The Intensity is a multiplier to the amount of generated corruption in a Blast.

It can represents: Bytes \(Nightmare, Distortion Engines\), Cheats \(Hellgenie, Freeze Engines\), Pipes \(Pipe Engine\), 32-bit floats \(Vector Engine\).

_Generally, the higher the Intensity is, the more corruption will happen_

Some engines have a configurable maximum number of concurrent elements as they can be very resource heavy. These elements get automatically discarded as newer ones get added.

This means that a Blast with 100 Intensity while Max Cheats is set to 50, the Blast will have the same result as 50.

##### Blast Radius

When a Blast is generated, RTC can target multiple Memory Domains. Changing the Blast Radius affects how corruption scatters across the selected Memory Domains.

SPREAD: Randomly spread across the Memory Domains.

CHUNK: Sent to one single zone that is randomly selected among the selected Memory Domains.

BURST: 10 Chunks of 1/10 of the total Intensity.

### Memory Domains

In Bizhawk, Memory Domains are the memory pools of the virtual chips in an emulated system. In RTC, they are wrapped within a proxy system that allows for keeping a hold of them when a system changes or to prevent certain unwanted scenarios from happening \(due to corruption\).

_Virtual Memory Domains can also coexist with Standard Memory Domains for that reason._

By default, RTC will select Memory Domains that are **Rewind-safe**, meaning that the data edited in these domains can be rewinded out of. Reverting back the corruption that occurs in domains that aren't rewind-safe requires to select "Reboot Core" in the emulation menu of BizHawk or reloading a Glitch Harvester Savestate or StashKey.

### Corruption Engines

#### Nightmare Engine

This engine corrupts on the raw Byte level.

_Effect: It changes Bytes in Memory once._

**Blast Type**

This parameter defines the effect applied on Byte

RANDOM: Will replace the Byte with a random Byte

RANDOMTILT: Will replace the Byte with a random Byte or Increments it or Decrements it.

TILT: Will Increment or Decrement a random Byte.

#### Hellgenie Engine

Uses the built-in BizHawk Cheat Engine to generate random Cheats.

Effect: It changes Bytes and forces them keep the value.

**Max Cheats**

Cheats are resource expensive as they re-write memory on every cycle and must be recycled. This allows you to define how many cheats are allowed. New cheats retire old ones.

**Clear cheats on Rewind**

Rewinding in BizHawk will force all cheats to be removed.

**Shuffle cheat values**

Clear all cheats

Clears all active cheats

#### Distortion Engine

This engine backups Bytes and restores those backups once, later in time.

_Effect: This corrupts data by restoring some of it back in time._

**Distortion Delay**

This is the amounts of steps that each corruption units has to wait before restoring a backup.

**Resync Distortion**

This erases all corruption units pending to be restored.

#### Freeze Engine

Uses the built-in BizHawk Cheat Engine to generate freeze addresses.

There is an odd quirk that will eventually be fixed: Currently only uses the RAM domain (predetermined by Bizhawk)

_Effect: It forces Bytes to keep their value._

**Max Freezes**

Freezes are resource expensive as they re-write memory on every cycle and must be recycled. This allows you to define how many freezes are allowed. New freezes retire old ones.

**Clear freezes on Rewind**

Rewinding in BizHawk will force all freezes to be removed.

#### Pipe Engine

This engines binds addresses together and can make data bleed from a memory domain to another. It uses Pipes, which route memory change on every Emulator Step \(or Corrupt Step\).

**Max Pipes**

Pipes are resource expensive as they move memory memory on every cycle and must be recycled. This allows you to define how many pipes are allowed. New pipes retire old ones.

**Lock Pipes**

Prevents any change to be done to the current Pipes.

**Generate Chained pipes**

By default, all pipes are generating in chain. this means two things: Pipe endpoints will collide and the first generated pipe in a BlastLayer will always be invalid. This can be observed when edited in the Blast Editor. Otherwise, this is the default behavior of the pipe engine.

When this setting is Off, the endpoint of a pipe will be randomly chosen among the Memory Domains in the same fashion as Blast Type SPREAD.

**Process on Emulator Step**

Disabling this causes the pipes to sync with the Corrupt Step instead of Emulator Step

**Clear pipes on Rewind**

Rewinding in BizHawk will force all pipes to be removed.

**Tilt Value**

This is a value modifier that takes place at the End of the pipe. The value \(negative or positive\) will be added to the piped value but will not affect the origin address.

#### Vector Engine

This engine works exclusively on 32bit+ systems that use IEEE 754 float values.

_Effect: Corrupts 32bit vectors_

**Limiter List**

On the generation of every Unit with this engine, the value at the randomly address is going to be compared to a list of legal values called a Limiter List. If the value at the random address isn't legal according to the list, the Unit then will not be part of the BlastLayer.

**Value List**

After generation of the Unit with this engine, a replacement value is assigned to the legal address. This value is randomly selected from a selected Value List.

**Lists**

Extended : -65536.00 to +65536.00 in low res, including tiny decimals

Extended+ : 0 to +65536 in low res, including tiny decimals

Extended- : 0 to -65536 in low res, including tiny decimals

Whole: -65536.00 to +65536.00 in low res, integral numbers

Whole+: 0 to +65536.00 in low res, integral numbers

Tiny: tiny decimals between -1.00 and +1.00

One: The number 1.00

One\*: The numbers 1.00 and -1.00

Two: The number 2.00

AnyFloat: Randomly generated Float, any address is legal

#### External ROM Plugin

RTC Supports daisy chaining from ROM Corruptors. Some popular ones have been modded to work seamlessly as plugins.

When a ROM Corruptor sends a corrupted ROM to RTC, a differential is calculated between the original and the corrupted one, then a BlastLayer is generated from that differential. Just like with other engines, the BlastLayer can be toggled ON and OFF when ran with RTC.



# Advanced Guide

## Glitch Harvester

The Glitch Harvester is one of the biggest features of RTC. It is simple to use, yet difficult to master.

Basic usage is fairly simple, you create a savestate, select the zones you would like to corrupt, chose an intensity and click the “Blast/Send” button, the emulator then corrupts the selected memory zones and instantly loads the savestate. \(The “Blast/Send” function can be bound to any key/button\)

### The interface

_This will explain the complex layout of interactive elements which makes the interface._

\[INSERT GLITCH HARVESTER SCREENSHOT WITH CLICKABLE AREAS\]

### Action Panel

#### Blast/Send

Blast/Send is the corruption button of the Glitch Harvester. It can corrupt, inject, replay and merge saved items. If _Stash Results_ is checked, it will create a new item in the Stash History box.

#### Send Raw to Stash

This will create a item in the Stash History box. The generated BlastLayer is applied \(Corruption occurs\) then a new Savestate is created for this item. Alterating corruption \(Cheats and Pipes\) will be stored in the attached BlastLayer but destructive corruption \(Byte changes\) will be compiled in the Savestate.

### Savestate Manager

**Change -&gt; SAVE/LOAD**

The change button flips the one on its right between SAVE and LOAD. This button toggling system is made this way to prevent accidental overwriting of Glitch Harvester Savestates.

The SAVE and LOAD are for saving and loading Glitch Harvester Savestates.

##### Numeric Buttons

Numeric buttons \(1-40\) are used to select a Glitch Harvester save-state slot.

An associated Textbox can be used for very short descriptions.

##### Back and Forward

This switches between pages of 10 Glitch Harvester Savestates.

##### Load on click

If checked, the Glitch Harvester will load a save state upon clicking on it.

##### Load/Save Savestate List

These buttons allow you to Save and Load the 40 Glitch Harvester Savestate slot to/from a file in a similar format to a Stockpile.

### Intensity

This control is linked to the intensity controls in the Main Window. It multiplies the amount of generated Units on every Blast.

### Action modifiers

The Corrupt, Inject and Original radio buttons will change the function of the Blast/Send button.

**Corrupt** is the default setting. Blast/Send will have its default behavior and loaded StashKeys will include corruption when replayed.

**Inject** will make the Blast/Send button load the corruption layer from the selected item in the Stash History or Stockpile Manager into the currently selected Glitch Harvester Savestate. The same action will happen when clicking on an item in the Stash History or Stockpile Manager.

**Original** will load the selected item from the Stash History or Stockpile Manager without the corruption layer.

### Action triggers

**Auto-Load State** makes it so a Savestate is loaded during Corruption or Replaying and item. When the _Corrupt_ modifier is selected, loading an item from the Stash History or Stockpile Manager will use the embedded Savestate in the StashKey. Otherwise, it comes from the selected item in the Savestate Manager.

**Load on select** causes the StashKey to be loaded when an item is selected from the Stash History or Stockpile Manager. When this option is unchecked, loading a selected item requires to press the Blast/Send button.

**Stash Results** makes it so generated corruption will be added to the Stash History upon generation of a BlastLayer. If a generated BlastLayer has 0 units, the StashKey will not be added to the Stash History.

#### BlastLayer Toggle

Attempts to uncorrupt/recorrupt the game on the fly. Results not guaranteed.

#### Reroll Selected

Rerolls the corruption values of the selected item in the Stash History or Stockpile. This allows to attempt to get better results from a corruption. The result will be sent in the Stash History.

### Render Output

This allows you quickly/automatically start audio/video rendering when corrupting using the Glitch Harvester. Rendered files will be saved in the “RENDEROUTPUT” folder which is in _BizHawk/RTC/RENDEROUTPUT_

**Render type** allows you to select a file format for rendering. If you're getting an error with AVI rendering, it might mean that no codec is selected in BizHawk. In order to do so, you must start an AVI rendering from BizHawk at least once.

**Render at load** will start the render when an item from the Stash History or Stockpile Manager is loaded.

### Stash History

This is where new corruptions are stashed. The items that appear there can be sent to a Stockpile using the button between the Stash History and Stockpile Manager.

### Stockpile Manager

This part of the Glitch Harvester is dedicated to edit and do operations onto Stockpiles.

The **Load** button allows you to either load a Stockpile or load a BizHawk Config file from an _SKS_ file.

_Loading a config file from a stockpile will keep your hotkeys and controller keybinds_

Using **Save as** and **Save** buttons will generate/overwrite an _SKS_ file that contains corruption data, roms and BizHawk Savestate. The _SKS_ file also contains the BizHawk config from the last person who saved it.

**Using someone's config file**

When replaying a stockpile, corruptions can appear different if there are differences in emulator core configurations. While RTC is able to detect core mismatches during loading, specific configuration differences are not.

Loading someone's config file pretty much guarantees that your BizHawk Emulator is in the same state as the person who saved the Stockpile. While your controller config might be lost during the time this config is loaded, it can be reverted afterwards by selecting the **Restore BizHawk config Backup** option from the Load menu.

**Importing Stockpile items**  
This button allows you to merge stockpiles together by importing them into the one currently edited.

**Merging StashKeys together**  
By holding CTRL and clicking on multiple Stockpile items, you can load and merge items together. The resulting item will be added to the Stash History.

Merging items together requires them to be for the same console and same game. The Savestate that is used in the merged result is from the first item that got selected.

## Stockpile Player


This is a minimalist version of the Glitch Harvester's Stockpile Manager. It allows you to load Stockpiles and replay corruptions.

The Previous and Next buttons are for jumping from a corruption to another. They do the same thing as clicking on the corruptions directly.

The Red refresh button replays the current corruption.

BlastLayer Button: Toggles ON/OFF the BlastLayer of the last executed StashKey, essentially attempting to uncorrupt/recorrupt in real-time.

If the button in the Note column has a ⚠ Symbol, it means that a note is attached to the corruption. Click on it to open the note.

Various options from RTC's Engine Config menu are present in a contextual menu if you right-click on corruptions.





## RTC Multiplayer

### Connecting RTCs together

Before connecting RTCs together, let this small fact known : RTC's Detached mode uses the same components as the Multiplayer mode in RTC. This is why you must run RTC in Attached mode in order to connect RTCs together.

** Session Settings **

RTC uses TCP port 42069 by default. You will need to open this port in your router if you plan on being the server. The client doesn't need it.

Simply start the multiplayer in the right category on order to start the server or connect to it.

You can also run TWO RTCs in Multiplayer on the same machine by connecting to "127.0.0.1" or simply leaving the case blank.

RTC's Multiplayer is fully bidirectional, meaning that both Client/Server can do exactly the same thing.

** Manual Commands **

There are 3 types of commands:
PUSH : Sends an item to the other RTC
PULL : Downloads an item from the other RTC
SWAP : Swaps items between the two RTCs

Command items
Game: Game ROM
State: Game's State
Screen: Picture of RTC's game's screen
BlastLayer: Last executed Corruption's Blast
StashKey: Last executed Corruption Item

** Video Streaming **

The Multiplayer screen and Stream options are for streaming a video feed between RTCs.

The screen can be popped out of the RTC Multiplayer options.

### Metagames and Multiplayer Features

** Game of Swap **

Both video streams will start. A red bar will start shrinking until it totally disappears. Once the red bar is gone, the two currently running games will be exchanged between RTCs.

** BlastBoard **

This is like a Soundboard, except that instead of sounds, it's Blasting the other RTC using the BlastLayers of the currently loaded Stockpile. You may wanna sanitize your corruptions using the Blast Editor before using this mode.

** Splitscreen **

This pops out the Multiplayer screen and attaches both Bizhawk feeds together in a new window.

This hides the default Bizhawk window so you'll want to stop Splitscreen before closing BizHawk.

# Expert Guide

## Hotkeys

**Manual Blast**

Does a normal Blast that doesn't get sent to the Glitch Harvester

**Auto-Corrupt**

Toggles ON/OFF on the Auto-Corrupt feature.

**Error Delay--**

Decreases the currently set Error Delay by 1

**Error Delay++**

Increases the currently set Error Delay by 1

**Intensity--**

Decreases the currently set Intensity by 1

**Intensity++**

Increases the currently set Intensity by 1

**GH Load and Corrupt**

Loads the selected GH Savestate, creates a StashKey in the Stash History and then runs it.

**GH Just Corrupt**

Creates a StashKey in the Stash History and then runs it without loading a save.

**GH Load**

Loads the currently selected Glitch Harvester Savestate Box.

**GH Save**

Saves the game state in the currently Glitch Harvester Savestate Box.

**Stash-&gt;Stockpile**

Sends the currently selected item in the Stash History and sends it to the Stockpile.

**Induce KS Crash**

Kills the KillSwitch heartbeat, causing \(if enabled\) RTC to detect a crash.

**Blast+RawStash**

Does a Manual Blast to the game then creates a Raw Stashkey in the Stash History.

**Send Raw to Stash**

Creates a Raw StashKey in the StashHistory

**BlastLayer Toggle**

Toggles ON/OFF the BlastLayer of the last executed StashKey

**BlastLayer Re-Blast**

Re-executes BlastLayer of the last executed StashKey.

## Blast Editor

Any StashKey in the Glitch Harvester can be opened in the Blast Editor by right-clicking on it and select _"Open Selected Item in Blast Editor"_.

A copy of the StashKey is done and every Unit from that BlastLayer is displayed in a list. Every line describes what will happen when that Unit is executed. There are panels on the right that allow you to edit certain values of the Unit and update them.

Double Clicking on an Unit will disable it as shown by the \[x\] that becomes \[ \]. You can also use the buttons on the right to quickly disable and enable Units.

**Sanitizing corruptions**

Corruptions can be sanitized in the Blast Editor to remove useless instructions that might break the game when ran. You can very easily isolate a corruption \(effect\) by doing the following:

\[Random Disable 50%\] then \[Load + Corrupt\].  
Is the corruption \(effect\) still present?  
If Yes -&gt; \[Remove Disabled\]  
If No -&gt; \[Invert Disabled\] then \[Remove Disabled\]

By repeating the steps above a certain amount of time, the useless instructions will progressively disappear. At some point you may need to manually enable and disable instructions in order to isolate what is part of the corruption and what is not.

**Note: All addresses and values are stored as decimal**

## Virtual Memory Domains

Virtual Memory Domains, also called VMDs, are virtual representations of areas from one or multiple real Memory Domains. The VMD Generator uses address instructions to make VMD Prototypes which can be used to generate/regenerate VMDs. These prototypes are very lightweight, save/load from a file and can also be created from a Corruption in the Glitch Harvester.

### Virtual Memory Domain Pool

The Virtual Memory Domain Pool is your main interaction window for loading and working with already loaded VMDs.

**Load VMD From File**

Allows you to load VMDs that were previously saved to a file.

**Save Selected VMD to File**

Allows you to save a generated VMD to a file which can be loaded later.

**Rename Selected VMD**

Allows you to rename a VMD.

**Unload Selected VMD**

Unloads the selected VMD from the RTC so it no longer appears in the Domain list and the VMD Pool.

**VMD Size**

Displays the size of the currently selected VMD in bytes.

**Real Domain**

Displays the memory domain that the VMD is built to target.

### Virtual Memory Domain Generator

**Load Domains**

Loads the Memory Domains of the currently active emulation core into the VMD Generator.

**Memory Domain**

This Selector Box allows you to chose a target Domain.

**Domain Size**

The size of the selected Memory Domain in bytes

**Word Size**

The size of a [word](https://en.wikipedia.org/wiki/Word_%28computer_architecture%29) for the currently selected memory domain

**Endian Type**

The [endian type](https://en.wikipedia.org/wiki/Endianness) for the currently selected memory domain

**Set pointer every X addresses**

Generates a VMD pointer every X addresses of the range input into the generator.

**VMD Name**

The name of the VMD being generated.

**Generate VMD**

Generates the VMD.

**Remove/Add Addresses**

The addresses that will be used in generation of your VMD. This box can take input in various forms. A single line is treated as a single command. You can use multiple commands in generation of the same VMD.

You are able to:

* Add an address range
  * Example: 50-100
* Add a single address
  * Example: 55
* Remove an address range
  * Example: -60-110
* Remove a single address
  * Example: -66

If the user doesn't add a value or range, the default range will be the entire selected memory domain. You are able to remove a value from this default range using one of the various remove methods. For example, if you only input "-55" into the box, you'd get a VMD which has every address in the real memory domain excluding -55.

**Additional notes:**

* By default, all addresses are treated as decimal
* If you add "0x" before an address, it will be treated as hexadecimal rather than decimal.
* Single added addresses will bypass the removal range.
* Single added addresses aren't affected by the pointer spacer parameter.
* Ranges are exclusive, which means that the last address will be excluded from the range.

## Generating Active Tables

Feature not reimplemented yet



## RTC Dev Discord

If you need advanced help, want to report bugs, ask features or even help with development, we have a development Discord server.

_This is a serious discord for sharing information, dev builds, report bugs and request features. It is not a playground._

####The rules are the following

→ Do not spam, post memes or cause trouble.

→ Keep the chat to bare minimum, prioritize big blocks of text over multiple posts (it makes them easier to delete if needed)

→ **#corruption_general** is for discussing of corruption-related things

→ **#corruption_showcase** is for sharing corruptions you made. Please focus on new discoveries and experiments with new features. Don't post SMB1 tileset vomit.

→ **#corruption_help** is for requesting help or any kind of support for corruption-related programs, technique and all sorts of issues. Use this channel to discuss about issues before reporting an actual bug.

→ **#bug_reporting** is for submitting confirmed bugs, provide screenshots and detailed instructions on how to reproduce the bug.

→ **#feature_request** is for requesting features. Make sure to provide as much details as possible about what you want.

→ The **#bug_reporting** and **#feature_request** channels are exclusive to VERIFIED power users. If you want to submit bugs or features, ask in **#corruption_help** and we'll see if that gets approved or not.

→ Your posts may get deleted. This server has to be sanitized sometimes, especially in the #bug_reporting and #feature_request channels.

→ Your requests may get erased and reposted in a stylized box.

→ **Keep your discussion related to RTC and other corruption software.**

→ **Some of our members have some online notoriety. I will gently ask you stay calm and polite when they are around and refrain from bugging them. Childish fanboyism is not tolerated.**

If you agree to the rules shown above, you can join at the link below

[I agree. Let me in](https://discord.gg/uzxHvUV) 
