### Real-Time Corruptor: Basic Guide

* [**Index**](#basic-guide)
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
      * [Custom Engine Precision](#custom-engine-precision)

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

AnyFloat: Randomly generated Float (Value) or any address is legal (Limiter)

[**Check RTC_VectorEngine.cs on Github for exact values of the lists**](https://github.com/ircluzar/RTC3/blob/master/Real-Time%20Corruptor/BizHawk_RTC/BizHawk.Client.EmuHawk/RTC/RTC_VectorEngine.cs) 

#### External ROM Plugin

RTC Supports daisy chaining from ROM Corruptors. Some popular ones have been modded to work seamlessly as plugins.

When a ROM Corruptor sends a corrupted ROM to RTC, a differential is calculated between the original and the corrupted one, then a BlastLayer is generated from that differential. Just like with other engines, the BlastLayer can be toggled ON and OFF when ran with RTC.

#### Custom Engine Precision

As of RTC 3.10, a with options for "Custom Precision" Has been added to most of the engines. Enabling the option and setting a value allows you to override the current core's default word size and corrupt differently. Previously, all engines generated corruption in 8-bit, no matter which system is being emulated.
