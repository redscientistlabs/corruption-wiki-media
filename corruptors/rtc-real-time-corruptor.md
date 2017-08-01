# Real-Time Corruptor for BizHawk

###### Author: [Phil Girard](http://redscientist.com/)

###### Source: [https://github.com/ircluzar/RTC3/](https://github.com/ircluzar/RTC3/)

###### Download: [http://redscientist.com/\#/rtc](http://redscientist.com/#/rtc)

The Real-Time Corruptor for BizHawk is a Dynamic Corruptor for emulated games. It's a mod to the Open Source BizHawk Emulator that works by modifying live data from virtual memory chips of emulated systems.

### Index

* [**Index**](#index "Literally this")
  * [**Quick Start**](#quick-start)
  * [**Fundamentals of RTC**](#fundamentals-of-rtc)
  * [**Basic**](#basic-guide)
    * [**RTC Vocabulary**](#rtc-vocabulary)
      * [Blast](#blast)
      * [Stockpile](#stockpile)
      * [StashKey](#stashkey)
      * [BlastLayer](#blastlayer)
    * [**General Parameters**](#general-parameters)
      * [Auto-Corrupt](#auto-corrupt)
      * [Error Delay](#error-delay)
      * [Intensity](#intensity)
      * [Blast Radius](#blast-radius)
    * [**Corruption Engines**](#corruption-engines)
      * [Nightmare Engine](#nightmare-engine)
      * [Hellgenie Engine](#hellgenie-engine)
      * [Distortion Engine](#distortion-engine)
      * [Freeze Engine](#freeze-engine)
      * [Pipe Engine](#pipe-engine)
      * [Vector Engine](#vector-engine)
      * [External ROM Plugin](#external-rom-plugin)
    * [**Main RTC Window**](#main-rtc-window)
    * [**Stockpile Player**](#stockpile-player)
  * [**Advanced**](#advanced-guide)
    * [Glitch Harvester](#glitch-harvester)
    * [RTC Multiplayer](#rtc-multiplayer)
    * [BizHawk Modifications](#bizhawk-modifications)
  * [**Expert**](#expert-guide)
    * [Virtual Memory Domains](#virtual-memory-domains)
    * [Generating Active Tables](#generating-active-tables)
    * [Editing BlastLayers](#editing-blastlayers)
  * [**Video Tutorials**](#video-tutorials)

##### Quick Start

The Real Time Corruptor was designed with ease of use in mind, if you want to get right into the action simply load a ROM and click “Easy Start” and you are away! \(_Instant results not always guaranteed\)_

##### Fundamentals of RTC

First, let’s go over the basic fundamentals of how this corruptor functions.

Video game corruption happens when an emulated video game whose program files were altered either in the emulated game’s memory \(RAM\) or in the ROM itself. A real-time corruption is when the corruption itself occurs while the game is running or when the effects can be altered on a time basis.

**RTC **is a mod for BizHawk, which means that any emulated system that BizHawk supports _should_ be compatible. Every system is detailed as a series of memory chips known as Memory Domains. The corruption will be generated for the selected domains in the main window. Certain engines/plugins may ignore the selected domains as part of their design.

What is usually known as an iteration in static corruptors, is called a Blast in the RTC. A blast consists of a series of operations that are to be applied in the data located on the emulated game’s memory banks. \(RAM, VRAM, ROM, etc.\)

**The Auto-Corrupt function **attaches the blast generation to the emulated game’s clock. Smaller blasts on a fast clock will create a constant flow of randomly generated corruption. This flow can be controlled by three parameters: The **Error Delay,** which is a divider linked to the game clock, The **Intensity **which is a multiplier for the number of corruption units to be generated \(which depends on the selected engine\). The **Blast Radius** determines how is the corruption is spread on the selected domains.

# Basic Guide

### RTC Vocabulary

##### Blast

A Blast is the action of generating and/or applying a BlastLayer item \(The action of corrupting\). When being generated, a Blast will contain a certain amount of corruption instructions. The amount of generated corruption instructions is defined by the Intensity setting.

RTC is built in a way that corruption is always generated and saved in cache before being applied. This allows replayability, manipulation and real-time interaction with these entities. When applied, byte-changing instructions usually backups values before modifying them. This allows corruption to be theorically disabled/reapplied on the fly, although this doesn't always work. Unit types that work by re-executing themselves such as Cheats and Pipes do not take backups. Instead, they simply get removed from their execution pools. This means that while their effect may be stopped in real-time, it also may not be completely reverted.

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

Item that represents a chip or memory pool on an emulated system.

### General Parameters

##### Auto-Corrupt

When this is enabled, RTC attempts to Generate and Execute a BlastLayer on every Emulation Step. The amount of corruption can be set by changing the Intensity and Error Delay settings.

_A Blast happens on every Corrupt Step_

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

TODO: Randomize all current cheat values

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

**Process on Emulator Step**

Disabling this causes the pipes to sync with the Corrupt Step instead of Emulator Step

**Clear pipes on Rewind**

Rewinding in BizHawk will force all pipes to be removed.

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

AnyFloat: Randomly generated Float

#### External ROM Plugin

RTC Supports daisy chaining from ROM Corruptors. Some popular ones have been modded to work seamlessly as plugins.

When a ROM Corruptor sends a corrupted ROM to RTC, a differential is calculated between the original and the corrupted one, then a BlastLayer is generated from that differential. Just like with other engines, the BlastLayer can be toggled ON and OFF when ran with RTC.

## Main RTC Window

## Stockpile Player

# Advanced Guide

## Glitch Harvester

### Introduction

The Glitch Harvester is one of the biggest features of RTC. It is simple to use, yet difficult to master.

Basic usage is fairly simple, you create a savestate, select the zones you would like to corrupt, chose an intensity and click the “Blast/Send” button, the emulator then corrupts the selected memory zones and instantly loads the savestate. \(The “Blast/Send” function can be bound to any key/button\)

### The interface

_This will explain the complex layout of interactive elements which makes the interface._

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

### Load/Save Savestate List

These buttons allow you to Save and Load the 40 Glitch Harvester Savestate slot to/from a file in a similar format to a Stockpile.

### Intensity

This control is linked to the intensity controls in the Main Window. It multiplies the amount of generated Units on every Blast.

#### Action modifiers

The Corrupt, Inject and Original radio buttons will change the function of the Blast/Send button.

**Corrupt** is the default setting. Blast/Send will have its default behavior and loaded StashKeys will include corruption when replayed.

**Inject** will make the Blast/Send button load the corruption layer from the selected item in the Stash History or Stockpile Manager into the currently selected Glitch Harvester Savestate. The same action will happen when clicking on an item in the Stash History or Stockpile Manager.

**Original** will load the selected item from the Stash History or Stockpile Manager without the corruption layer.

#### Action triggers

**Auto-Load State** makes it so a Savestate is loaded during Corruption or Replaying and item. When the _Corrupt_ modifier is selected, loading an item from the Stash History or Stockpile Manager will use the embedded Savestate in the StashKey. Otherwise, it comes from the selected item in the Savestate Manager.

**Load on select** causes the StashKey to be loaded when an item is selected from the Stash History or Stockpile Manager. When this option is unchecked, loading a selected item requires to press the Blast/Send button.

**Stash Results** makes it so generated corruption will be added to the Stash History upon generation of a BlastLayer. If a generated BlastLayer has 0 units, the StashKey will not be added to the Stash History.

#### BlastLayer On/Off

Attempts to uncorrupt/recorrupt the game on the fly. Results not guaranteed.

#### Reroll Selected

Rerolls the corruption values of the selected item in the Stash History or Stockpile. This allows to attempt to get better results from a corruption. _This operation is permanent on the StashKey and cannot be undone._

### Render Output

This allows you quickly/automatically start audio/video rendering when corrupting using the Glitch Harvester. Rendered files will be saved in the “RENDEROUTPUT” folder which is in _BizHawk/RTC/RENDEROUTPUT_

**Render type** allows you to select a file format for rendering. If you're getting an error with AVI rendering, it might mean that no codec is selected in BizHawk. In order to do so, you must start an AVI rendering from BizHawk at least once.

**Render at load** will start the render when an item from the Stash History or Stockpile Manager is loaded.

### Stash History

This is where new corruptions are stashed. The items that appear there can be sent to a Stockpile using the button between the Stash History and Stockpile Manager.

### Stockpile Manager

This part of the Glitch Harvester is dedicated to edit and do operations onto Stockpiles.

The **Load** button allows you to either load a Stockpile or load a BizHawk Config file from an _SKS_ file.

Using **Save as** and **Save** buttons will generate/overwrite an _SKS_ file that contains corruption data, roms and BizHawk Savestate. The _SKS_ file also contains the BizHawk config from the last person who saved it.

**Using someone's config file**

When replaying a stockpile, corruptions can appear different if there are differences in emulator core configurations. While RTC is able to detect core mismatches during loading, specific configuration differences are not.

Loading someone's config file pretty much guarantees that your BizHawk Emulator is in the same state as the person who saved the Stockpile. While your controller config might be lost during the time this config is loaded, it can be reverted afterwards by selecting the **Restore BizHawk config Backup** option from the Load menu.

**Importing Stockpile items**  
This button allows you to merge stockpiles together by importing them into the one currently edited.

**Merging StashKeys together**  
By holding CTRL and clicking on multiple Stockpile items, you can load and merge items together. The resulting item will be added to the Stash History.

Merging items together requires them to be for the same console and same game. The Savestate that is used in the merged result is from the first item that got selected.

