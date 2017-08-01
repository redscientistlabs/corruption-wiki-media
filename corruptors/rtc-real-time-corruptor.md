# Real-Time Corruptor for Bizhawk

###### Author: [Phil Girard](http://redscientist.com/)

###### Source: [https://github.com/ircluzar/RTC3/](https://github.com/ircluzar/RTC3/)

###### Download: [http://redscientist.com/#/rtc](http://redscientist.com/#/rtc)


The Real-Time Corruptor for BizHawk is a Dynamic Corruptor for emulated games. It's a mod to the Open Source BizHawk Emulator that works by modifying live data from virtual memory chips of emulated systems.

### Index

* [**Index**](#index "Literally this")
    * [Quick Start](#quick-start)
    * [Fundamentals of RTC](#fundamentals-of-rtc)
    * [**Basic**](#basic-guide)
        * [**RTC Concepts**](#rtc-concepts)
            * [Stockpile](#stockpile)
            * [Stash Key](#stash-key)
            * [Blast Layer](#blastlayer)
        * [**General Parameters**](#general-parameters)
            * [Blast](#blast)
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
    * [**Advanced**](#advanced-guide)
        * [Glitch Harvester](#glitch-harvester)
        * [RTC Multiplayer](#rtc-multiplayer)
        * [Bizhawk Modifications](#bizhawk-modifications)
    * [**Expert**](#expert-guide)
        * [Virtual Memory Domains](#virtual-memory-domains)
        * [Generating Active Tables](#generating-active-tables)
        * [Editing Blast Layers](#editing-blast-layers)
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

### RTC Concepts

##### Stockpile

Object that contains Corruptions (Stashkeys). It can be saved as a binary file that can include Game Binaries, Game States, Stash Keys and information related to BizHawk emulator cores, plugins and config.

Stockpiles can be managed using the Glitch Harvester's Stockpile Manager. Stockpiles can be replayed using the Stockpile Player or the Glitch Harvester.

##### Stash Key

Object that contains information about a game, its game state and an attached Blast Layer.

Corrupting using the Glitch Harvester can generate Stash Keys in the Stash History. They can later be manipulated and/or added to a Stockpile.

##### Blast Layer

Object that contains corruption instructions generated from a corruption engine.

BlastLayers that are ran from inside the Stockpile Player or the Glitch Harvester can be deactivated and reactivated on the fly. The program will attempt to uncorrupt a game while it runs. Results not guarantees.

##### Memory Domain

Object that represents a chip or memory pool on an emulated system.

### General Parameters

##### Blast

A corruption in RTC is usually called a Blast. A Blast is the action of generating and/or applying a BlastLayer. When being generated, a Blast will contain a certain amount of corruption instructions where this amount is defined by the currently selected Intensity.

##### Auto-Corrupt

When this is enabled, RTC attempts to Generate and Execute a Blast Later on every Emulation Step. The amount of corruption can be set by changing the Intensity and Error Delay settings.

*A Blast is done on every Corrupt Step*

##### Error Delay

→Only Applicable to AutoCorrupt

The Error Delay is a divider to the amount of generated corruption. This defines Auto-Corrupt will Blast the game every X steps.

Every Emulator Step that causes Auto-Corrupt to Blast is called a Corrupt Step.

##### Intensity

The Intensity is a multiplier to the amount of generated corruption in a Blast.

It can represents: Bytes (Nightmare, Distortion Engines), Cheats (Hellgenie, Freeze Engines), Pipes (Pipe Engine), 32-bit floats (Vector Engine).

*Generally, the higher the Intensity is, the more corruption will happen*

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

*Effect: It changes Bytes in Memory once.*

**Blast Type**

This parameter defines the effect applied on Byte

RANDOM: Will replace the Byte with a random Byte

RANDOMTILT: Will replace the Byte with a random Byte or Increments it or Decrements it.

TILT: Will Increment or Decrement a random Byte.

#### Hellgenie Engine

Uses the built-in Bizhawk Cheat Engine to generate random Cheats.

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

*Effect: This corrupts data by restoring some of it back in time.*

**Distortion Delay**

This is the amounts of steps that each corruption units has to wait before restoring a backup.

**Resync Distortion**

This erases all corruption units pending to be restored.

#### Freeze Engine

Uses the built-in BizHawk Cheat Engine to generate freeze addresses.

*Effect: It forces Bytes to keep their value.*

**Max Freezes**

Freezes are resource expensive as they re-write memory on every cycle and must be recycled. This allows you to define how many freezes are allowed. New freezes retire old ones.

**Clear freezes on Rewind**

Rewinding in BizHawk will force all freezes to be removed.

#### Pipe Engine

This engines binds addresses together and can make data bleed from a memory domain to another. It uses Pipes, which route memory change on every Emulator Step (or Corrupt Step).


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

*Effect: Corrupts 32bit vectors*

**Limiter List**

On the generation of every Unit with this engine, the value at the randomly address is going to be compared to a list of legal values called a Limiter List. If the value at the random address isn't legal according to the list, the Unit then will not be part of the Blast Layer.

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

One*: The numbers 1.00 and -1.00

Two: The number 2.00

AnyFloat: Randomly generated Float

#### External ROM Plugin

RTC Supports daisy chaining from ROM Corruptors. Some popular ones have been modded to work seamlessly as plugins.

When a ROM Corruptor sends a corrupted ROM to RTC, a differential is calculated between the original and the corrupted one, then a Blast Layer is generated from that differential. Just like with other engines, the BlastLayer can be toggled ON and OFF when ran with RTC.

# Advanced Guide

 ## Glitch Harvester
 
*Savestate-oriented corruption operator interface*

##EARLY WORK IN PROGRESS DOCUMENTATION

### Introduction

The Glitch Harvester is one of the biggest features of RTC. It is simple to use, yet difficult to master. 

Basic usage is fairly simple, you create a savestate, select the zones you would like to corrupt, chose an intensity and click the “Blast/Send” button, the emulator then corrupts the selected memory zones and instantly loads the savestate. (The “Blast/Send” function can be bound to any key/button)

### The interface

*This will explain the complex layout of interactive elements which makes the interface.*

### Action Panel

#### Blast/Send
Blast/Send is the corruption button of the Glitch Harvester. It can corrupt, inject, replay and merge saved items. If *Stash Results* is checked, it will create a new item in the Stash History box.

#### Send Raw to Stash
This will create a item in the Stash History box. The generated Blast Layer is applied (Corruption occurs) then a new Savestate is created for this item. Alterating corruption (Cheats and Pipes) will be stored in the attached Blast Layer but destructive corruption (Byte changes) will be compiled in the Savestate.

### Savestate Manager

**Change -> SAVE/LOAD**

The change button flips the one on its right between SAVE and LOAD. This button toggling system is made this way to prevent accidental overwriting of Glitch Harvester Savestates.

The SAVE and LOAD are for saving and loading Glitch Harvester Savestates.

##### Numeric Buttons
Numeric buttons (1-40) are used to select a Glitch Harvester save-state slot.

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

**Corrupt** is the default setting. Blast/Send will have its default behavior and loaded Stash Keys will include corruption when replayed.

**Inject** will make the Blast/Send button load the corruption layer from the selected item in the Stash History or Stockpile Manager into the currently selected Glitch Harvester Savestate. The same action will happen when clicking on an item in the Stash History or Stockpile Manager if the Load on select checkbox is selected.

Original will load the state from Stash and stockpile without the corruption layer.

#### Action triggers

Auto-Load State will automatically load the state before applying the corruption when the “Blast/Send” button is pressed.

Load on select toggles (on/off) if a Stash and Stockpile item will be loaded on selection.

Stash Corrupted, while enabled, will stash corrupted states into the Stash History.

Stash Injected, while enabled, will stash injected states into the Stash History.

Backup History will be included in the Restore data (Warning: Can cause slow-downs).

Turbo Switch toggles (on/off) the corruption layer on the fly. Results not guaranteed.

Render at load will start the render when a stash/stockpile item is loaded. 

Render at corrupt will start rendering when Corrupted or Injected.

Render options allows you to select the format type of the file that will be saved in the “RENDEROUTPUT” folder.

Stash History contains all the backed states that were corrupted/injected.

Current Stockpile contains hand-selected states that were corrupted/injected.

Select Multiple allows you to select multiple stockpile items and merge them with the Merge “Blast/Send” button.

Move Up and Move Down allows you to rearrange the order of the stockpile.

Add Stash to Stockpile takes the selected item in the Stash History and sends it in the Current Stockpile (Will display naming prompt).

Import Stockpile imports the contents of a selected stockpile into the Current stockpile.

Save/Load Stockpile save and loads the Current Stockpile into a file on your hard drive.

