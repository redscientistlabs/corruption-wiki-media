## Real-Time Corruptor for Bizhawk

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
            * [Stash Key](#stashkey)
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

## Basic Guide

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

General Parameters

##### Blast

A corruption in RTC is usually called a Blast. A Blast is the action of generating and/or applying a BlastLayer. When being generated, a Blast will contain a certain amount of corruption instructions where this amount is defined by the currently selected Intensity.

##### Auto-Corrupt

When this is enabled, RTC attempts to Generate and Execute a Blast Later on every Emulation Step. The amount of corruption can be set by changing the Intensity and Error Delay settings.

A Blast is done on every Corrupt Step

##### Error Delay

→Only Applicable to AutoCorrupt

The Error Delay is a divider to the amount of generated corruption. This defines Auto-Corrupt will Blast the game every X steps.

Every Emulator Step that causes Auto-Corrupt to Blast is called a Corrupt Step.

##### Intensity

The Intensity is a multiplier to the amount of generated corruption in a Blast.

It can represents: Bytes (Nightmare, Distortion Engines), Cheats (Hellgenie, Freeze Engines), Pipes (Pipe Engine), 32-bit floats (Vector Engine).

Generally, the higher the Intensity is, the more corruption will happen

Some engines have a configurable maximum number of concurrent elements as they can be very resource heavy. These elements get automatically discarded as newer ones get added.

This means that a Blast with 100 Intensity while Max Cheats is set to 50, the Blast will have the same result as 50.

##### Blast Radius

When a Blast is generated, RTC can target multiple Memory Domains. Changing the Blast Radius affects how corruption scatters across the selected Memory Domains.

SPREAD: Randomly spread across the Memory Domains.

CHUNK: Sent to one single zone that is randomly selected among the selected Memory Domains.

BURST: 10 Chunks of 1/10 of the total Intensity.
