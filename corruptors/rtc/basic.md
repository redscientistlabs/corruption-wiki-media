# Basic Guide

### Real-Time Corruptor: Basic Guide

* **Index**
  * \*\*\*\*[**RTC Concepts and vocabulary**](basic.md#rtc-concepts-and-vocabulary)\*\*\*\*
    * [Vanguard](basic.md#vanguard)
    * [BlastUnit](basic.md#blastunit)
    * [BlastLayer](basic.md#blastlayer)
    * [Blast](basic.md#blast)
    * [StashKey](basic.md#stashkey)
    * [Stockpile](basic.md#stockpile)
    * [Memory Domain](basic.md#memory-domain)
    * [Virtual Memory Domain](basic.md#virtual-memory-domain)
    * [Emulation Step](basic.md#emulation-step)
    * [Active Units and Infinite Units](basic.md#active-units-and-infinite-units)
  * \*\*\*\*[**General Parameters**](basic.md#general-parameters)\*\*\*\*
    * [Auto-Corrupt](basic.md#auto-corrupt)
    * [Manual Blast](basic.md#manual-blast)
    * [Error Delay](basic.md#error-delay)
    * [Intensity](basic.md#intensity)
    * [Blast Radius](basic.md#blast-radius)
  * \*\*\*\*[**BizHawk: Rewindable Memory Domains**](basic.md#bizhawk-rewindable-memory-domains)\*\*\*\*
  * \*\*\*\*[**Corruption Engines**](basic.md#corruption-engines)\*\*\*\*
    * [Nightmare Engine](basic.md#nightmare-engine)
    * [Hellgenie Engine](basic.md#hellgenie-engine)
    * [Freeze Engine](basic.md#freeze-engine)
    * [Distortion Engine](basic.md#distortion-engine)
    * [Pipe Engine](basic.md#pipe-engine)
    * [Vector Engine](basic.md#vector-engine)
    * [Lists](basic.md#lists)
    * [Custom Engine](basic.md#custom-engine)
    * [Engine Precision and alignment](basic.md#engine-precision-and-alignment)
  * [Auto-KillSwitch](basic.md#auto-killswitch)
  * [Game Protection](basic.md#game-protection)

## RTC Concepts and vocabulary

Before tackling how the corruptor is used, it is recommended to take some time to read the following details about the internals of RTC. These terms are going to be used throughout the entire guide.

#### Vanguard

Throughout this entire guide, Emulators and other programs that interface with RTC can be referenced as "Vanguard Implementations". This comes from the fact that RTC, as of version 5, uses a technology called Vanguard in order to bridge any program with RTC, therefore giving it control over its memory. In order for an emulator to interface in Real-Time with RTC, it must be modded with Vanguard and adhere to its API.

#### BlastUnit

_This represents one Unit of corruption instructions._

The BlastUnit's behavior is defined by the engine that generated it and may contain one or many Addresses, Values and extra parameters. Said behavior can be customized through the [Custom Engine](basic.md#custom-engine).

#### BlastLayer

_Type of item that contains_ [_BlastUnits_](basic.md#blastunit) _generated from a_ [_corruption engine_](basic.md#corruption-engines)_._

A BlastLayer is usually encapsulated within a [StashKey](basic.md#stashkey) and can be manipulated using the [Blast Editor](expert/blast-generator.md) or by merging multiple BlastLayers in the Glitch Harvester's Stockpile Manager. It can also be appended to another Savestate by using the Inject function of the [Glitch Harvester](advanced.md#glitch-harvester).

BlastLayers that are ran from the [Stockpile Player](advanced.md#stockpile-player) or from the [Glitch Harvester](advanced.md#glitch-harvester) can be deactivated and reactivated on the fly \(if applicable\).

#### Blast

_A Blast is the action of generating and/or applying a_ [_BlastLayer_](basic.md#blastlayer) _item \(The action of corrupting\)._

When being generated, a Blast will contain a certain amount of [BlastUnits](basic.md#blastunit). The amount of generated corruption Units is defined by the Intensity setting. The behavior of generated [units ](basic.md#blastunit)can be tweaked by changing the [selected Engine](basic.md#corruption-engines) or building a custom behavior in the [Custom Engine](basic.md#custom-engine).

RTC is built in a way that corruption is always generated and saved in memory before being applied. This allows replayability, manipulation and real-time interaction. When applied, byte-changing instructions usually backup values before modifying them. This allows corruption to be theoretically [disabled/reapplied on the fly](advanced.md#blastlayer-on-off), although this doesn't always work. [Certain types of units](basic.md#active-units-and-infinite-units) do not store backups. Instead, they simply get removed from their execution pools. This means that while their effect may be stopped in real-time, it also may not be completely reverted.

#### StashKey

_Type of item that contains information about a game, its game state and an attached_ [_BlastLayer_ ](basic.md#blastlayer)_\(Corruption instructions\)._

Corrupting using the [Glitch Harvester](advanced.md#glitch-harvester) generates StashKeys and sends them in the [Stash History](advanced.md#stash-history). They can later be manipulated and/or added to a [Stockpile](basic.md#stockpile).

#### Stockpile

_Type of item that contains_ [_StashKeys_](basic.md#stashkey)_._

It can be saved as a file that includes Stockpile items, Game Binaries, Savestates, corruption instructions, and information related to the targeted program, plugins and config. It is worth noting that saving stockpiles do not save game binaries by default. You must select "Include referenced files" in the [Glitch Harvester](advanced.md#glitch-harvester) in the Stockpile options.

Stockpiles can be managed using the [Glitch Harvester](advanced.md#glitch-harvester).

Stockpiles can be replayed using the [Stockpile Player](advanced.md#stockpile-player).

#### Memory Domain

_Item that represents a chip or memory pool on an emulated system._

Memory Domains wrap the native memory areas into our own format. Every [Vanguard Implementation](basic.md#vanguard) has to wrap memory areas in these interfaces, which allows in return for a complete control by RTC. The high-level Memory Domain interface also allows for them to coexist with Virtual Memory Domains, which are a higher level of abstraction on top of normal Memory Domains.

#### Virtual Memory Domain

_Item that represents continuous or non-contiguous part\(s\) of one or many Memory Domains_

Virtual Memory Domains are abstract lists of pointers that act as a Memory Domain. Most of the tools won't know the difference between a normal Memory Domain and a VMD. VMDs are marked with \[V\] to show that they are not real. They can be saved and generated from files and formulas. [BlastLayers](basic.md#blastlayer) can also be converted into VMDs.

_More information about Virtual Memory Domains is available in the_ [_VMD Guide_](expert/vmd-generator.md)\_\_

#### Emulation Step

[Vanguard implementations](basic.md#vanguard) are hooked to their emulator's clock using some sort of CPU loop. This means that RTC's clock is tied the game on a frame basis. Pausing the emulator causes this loop to also get paused, therefore halting any automatic generation of corruption.

#### Active Units and Infinite Units

As of version 5, RTC's [BlastUnit ](basic.md#blastunit)format is completely programmable and is able to do faithfully replace every BlastUnit type from the previous versions. Among the available behaviors, Units can be Active, meaning that they will have an effect for a certain amount of time and they can be Infinite if that time never runs out.

## General Parameters

#### Auto-Corrupt

When this is enabled, RTC will attempt to Generate and Execute a [BlastLayer](basic.md#blastlayer) on every [Emulation Step](basic.md#emulation-step). The amount of corruption can be set by changing the [Intensity](basic.md#intensity) and [Error Delay](basic.md#error-delay) settings.

#### Manual Blast

_Alternatively to_ [_Auto-Corrupt_](basic.md#auto-corrupt)_, Blasting a game with corruption can be triggered manually._

Blasts with a bigger [Intensity ](basic.md#intensity)can be as effective as a controlled stream of corruption. It does give the user more control on when the game is altered.

#### Error Delay

_→ Only Applicable to_ [_AutoCorrupt_](basic.md#auto-corrupt)\_\_

The Error Delay is a divider to the amount of generated corruption. This defines Auto-Corrupt will Blast the game every X [steps](basic.md#emulation-step).

_Example of how generation works with Error Delay:  
1 second @ 60fps with Intensity 500 and Error Delay 1 will generate 30k units  
1 second @ 60fps with Intensity 30k and Error Delay 60 will generate 30k units.  
The difference is that the first one will generate a constant stream of units while the second one will generate a big block of units every second._

_It should be worth noting the tweaking the Error Delay is NOT necessary to get corruption results. It only serves as a way to space out blasts during auto-corrupt._

#### Intensity

The Intensity is a multiplier to the amount of generated [Units ](basic.md#blastunit)in a [Blast](basic.md#blast)

_Generally, the higher the Intensity is, the more corruption will happen_

Some [engines ](basic.md#corruption-engines)generate [Active Units](basic.md#active-units-and-infinite-units), which execute code on every frame while they're active. There's a maximum amount of 50 active units by default. This setting can be changed in the engine settings \(when applicable\) or in Settings and tools -&gt; Corruption Settings

_This means that a Blast with 100 Intensity while Max Active Units is set to 50 will have the same result as a blast with 50 intensity, given that the currently selected engine generates Active Units._

#### Blast Radius

When a Blast is generated, RTC can target multiple [Memory Domains](basic.md#memory-domain) at once. Changing the Blast Radius affects how corruption scatters across the selected Memory Domains.

Spread: Randomly spread across the Memory Domains.

Chunk: Sent to one single zone that is randomly selected among the selected Memory Domains.

Burst: 10 Chunks of 1/10 of the total Intensity.

Even: Apply the blasts evenly spread through all selected domains.

Proportional: Apply the blasts proportionally through all selected domains based on the sizes

Normalized: Iterate through all selected domains and apply as intensity/\(size of largest domain / size of current domain\)

### BizHawk: Rewindable Memory Domains

In BizHawk, all emulator cores come with Rewind capabilities. At the time of writing this guide, no other emulator than BizHawk supports native Rewind \(among the ones modded with [Vanguard](basic.md#vanguard)\).

By default, RTC will select [Memory Domains](basic.md#memory-domain) that are **Rewind-safe**, meaning that the data edited in these domains can be rewinded out of. Reverting back the corruption that occurs in domains that aren't rewind-safe requires to select "Reboot Core" in the emulation menu of BizHawk or reloading a [Glitch Harvester Savestate](advanced.md#savestate-manager) or [StashKey](basic.md#stashkey).

It should be worth noting that RTC's Game Protection feature can act as a pseudo-rewind as it allows the user to jump back in the past using savestates. This feature should be available to any emulator with a Real-Time [vanguard implementation](basic.md#vanguard).

## Corruption Engines

_These are the various Engine Templates that you can use for corrupting games. These can be customized in the Custom Engine, in which you can load a template to work from._

### Nightmare Engine

![](../../.gitbook/assets/image%20%2838%29.png)

This engine corrupts on the raw byte level.

_Effect: It changes Bytes in Memory once._

**Blast Type**

This parameter defines the effect applied on Byte\(s\)

RANDOM: Will replace the Byte\(s\) at the selected address with random Byte\(s\)

RANDOMTILT: Will replace the Byte\(s\) with random Byte\(s\) or Increments it or Decrements it.

TILT: Will Increment or Decrement random Byte\(s\).

### Hellgenie Engine

![](../../.gitbook/assets/image%20%2828%29.png)

This engine generate Active Units, which execute on every frame. The Hellgenie Engine replicates the effect of Cheats \(see Game Genie, Active Replay, GameShark\) and replaces a value with a randomly selected one then applies it on every frame.

Effect: It randomly selects a value and forces a selected address to then keep that value.

**Max infinite units**

Infinite Units are resource expensive as they re-write memory on every frame and must be recycled. This allows you to define how many infinite units are allowed. New units retire old ones.

**Clear units on rewind**

Rewinding will clear all [infinite units](basic.md#active-units-and-infinite-units) that have an infinite life time \(when applicable\).

### Freeze Engine

![](../../.gitbook/assets/image%20%2848%29.png)

This engine generate Active Units, which execute on every frame. The Freeze Engine replicates the effect of Cheats \(see Game Genis, Active Replay, GameShark\) and replaces a value on every frame. The difference between this engine and the Hellgenie Engine is that this doesn't generate a value but instead keeps the value at the target adress and reapplies it on every frame, therefore freezing it into places.

_Effect: It forces Bytes at a selected address to keep their value._

**Max infinite units**

Infinite Units are resource expensive as they re-write memory on every frame and must be recycled. This allows you to define how many infinite units are allowed. New units retire old ones.

**Clear units on rewind**

Rewinding will clear all [infinite units](basic.md#active-units-and-infinite-units) that have an infinite life time \(when applicable\).

### Distortion Engine

![](../../.gitbook/assets/image%20%2824%29.png)

This engine backups Bytes and restores those backups once, later in time.

_Effect: This corrupts data by restoring some of it back in time._

**Distortion Delay**

This is the amounts of steps that each corruption unit has to wait before restoring a backup.

**Resync Distortion**

This erases all current [active units](basic.md#active-units-and-infinite-units) pending to be restored.

### Pipe Engine

![](../../.gitbook/assets/image%20%2825%29.png)

This engine generates units that bind addresses together and can make data bleed from a Memory Domain to another. It uses Infinite Units that route memory changes on every Emulator Step or frame.

**Lock Step units**

Prevents any change to be done to the current Active Units

**Clear units on rewind**

Rewinding will clear all [infinite units](basic.md#active-units-and-infinite-units) that have an infinite life time \(when applicable\).

### Vector Engine

![](../../.gitbook/assets/image%20%285%29.png)

This engine works exclusively on 32bit systems that use IEEE 754 float values.

If you need to use lists of a [precision ](basic.md#engine-precision-and-alignment)different than 32-bit, you must use the Custom Engine.

_Effect: Corrupts 32bit vectors_

**Limiter List**

On the generation of every Unit with this engine, the value at the randomly selected address is going to be compared to a list of legal values called a Limiter List. If the value at the random address isn't legal according to the list, the Unit then will not be part of the BlastLayer.

**Value List**

After generation of the Unit with this engine, a replacement value is assigned to the legal address. This value is randomly selected from a selected Value List.

### **Lists**

Extended : -65536.00 to +65536.00 in low res, including tiny decimals

Extended+ : 0 to +65536 in low res, including tiny decimals

Extended- : 0 to -65536 in low res, including tiny decimals

One: The numbers 1.00 and -1.00

One-: The number -1.00

One+: The number 1.00

Tiny: tiny decimals between -1.00 and +1.00

Two+: The number 2.00

Whole: -65536.00 to +65536.00 in low res, integral numbers

Whole+: 0 to +65536.00 in low res, integral numbers

_You can add your own lists using the List Generator Tool._

### Custom Engine

![](../../.gitbook/assets/image%20%2826%29.png)

This engine allows you to mix and match parameters to create your own engine.

See the [Custom Engine Guide](expert/custom-engine.md) for more information about it.

### Engine Precision and Alignment

![](../../.gitbook/assets/image%20%2844%29.png)

Allows you to choose what size BlastUnit will be generated. 8-bit \(one byte\), 16-bit \(2 bytes\), 32-bit \(4 bytes\) or 64-bit \(8 bytes\).

The alignment settings should always be left at 0 unless corruption is done on an experimental target, file or if the game that's being corrupted mispositions its data.

## Auto-KillSwitch

![](../../.gitbook/assets/image%20%282%29.png)

In order to give the user, the smoothest experience, RTC will constantly monitor the state of the [Vanguard-modded](basic.md#vanguard) emulator and attempt to kill it if it falls into a non-responsive state.

_If the heartbeat between RTC and the emulator stops for a long period, the progress bar will indicate the remaining time before the KillSwitch fires automatically._

While many emulators can have their games crash gracefully, they can sometimes freeze or enter an infinite loop if the game crash couldn't be handled properly. This can be detected and RTC will then proceed to kill and restart said emulator.

_When the Auto-KillSwitch is triggered, the user will hear a sound of broken plates, confirming that the emulator has been terminated. Said sound can be changed, replaced or muted in the Settings and tools._

## Game Protection

![](../../.gitbook/assets/image%20%2840%29.png)

The Game Protection optional feature has 2 benefits for the user:

* Keeps regular backups of the game's state in case of a crash
* Allows for a pseudo-rewind feature that works across all Real-Time Implementations

If the emulator crashes while Game Protection is enabled and there's at least one saved item, the game will reload the most recent state when it comes back up.

The Back/Now buttons allow for the user to browse the constantly updating list of savestates in order to rewind back, similarly to BizHawk's rewind feature but in bigger chunks of time.

_It should be worth noting that Game Protection increase the power requirements for a smooth experience. An SSD is required to prevent "hitching", although this is not always the case with every emulator/core. Mileage may vary._

