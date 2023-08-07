# Concepts and Vocabulary

Before tackling how the corruptor is used, it is recommended to take some time to read the following details about the internals of RTC. These terms are going to be used throughout the entire guide.

### Vanguard

Throughout this entire guide, Emulators and other programs that interface with RTC can be referenced as "Vanguard Implementations". This comes from the fact that RTC, as of version 5, uses a technology called Vanguard in order to bridge any program with RTC, therefore giving it control over its memory. In order for an emulator to interface in Real-Time with RTC, it must be modded with Vanguard and adhere to its API.

### BlastUnit

_This represents one Unit of corruption instructions._

The BlastUnit's behavior is defined by the engine that generated it and may contain one or many Addresses, Values and extra parameters. Said behavior can be customized through the Custom Engine.

### BlastLayer

_Type of item that contains_ [_BlastUnits_](concepts-and-vocabulary.md#blastunit) _generated from a_ [_corruption engine_](corruption-engines.md)_._

A BlastLayer is usually encapsulated within a [StashKey](concepts-and-vocabulary.md#stashkey) and can be manipulated using the [Blast Editor](blast-editor.md) or by merging multiple BlastLayers in the Glitch Harvester's Stockpile Manager. It can also be appended to another Savestate by using the Inject function of the [Glitch Harvester](glitch-harvester.md#glitch-harvester).

BlastLayers that are run from the [Stockpile Player](glitch-harvester.md#stockpile-player) or the [Glitch Harvester](glitch-harvester.md#glitch-harvester) can be deactivated and reactivated on the fly (if applicable).

### Blast

_A Blast is the action of generating and/or applying a_ [_BlastLayer_](concepts-and-vocabulary.md#blastlayer) _item (The action of corrupting)._

When being generated, a Blast will contain a certain amount of [BlastUnits](concepts-and-vocabulary.md#blastunit). The amount of generated corruption Units is defined by the Intensity setting. The behavior of generated units can be tweaked by changing the selected Engine or building a custom behavior in the Custom Engine.

RTC is built in a way that corruption is always generated and saved in memory before being applied. This allows replayability, manipulation, and real-time interaction. When applied, byte-changing instructions usually backup values before modifying them. This allows corruption to be theoretically [disabled/reapplied on the fly](glitch-harvester.md#blastlayer-on-off), although this doesn't always work. Certain types of units do not store backups. Instead, they simply get removed from their execution pools. This means that while their effect may be stopped in real-time, it also may not be completely reverted.

### StashKey

_Type of item that contains information about a game, its game state, and an attached_ [_BlastLayer_ ](concepts-and-vocabulary.md#blastlayer)_(Corruption instructions)._

Corrupting using the [Glitch Harvester](glitch-harvester.md) generates StashKeys and sends them in the [Stash History](glitch-harvester.md#stash-history). They can later be manipulated and/or added to a [Stockpile](concepts-and-vocabulary.md#stockpile).

### Stockpile

_Type of item that contains_ [_StashKeys_](concepts-and-vocabulary.md#stashkey)_._

Stockpiles are saved files that contain Stockpile items, Game Binaries, Savestates, corruption instructions, and information related to the targeted program, plugins, and config. It is worth noting that Stockpiles will contain Game Binaries by default. This means it is important to deselect "Include referenced files" in the Stockpile Manager of the [Glitch Harvester](glitch-harvester.md#glitch-harvester) when sharing Stockpiles online is the goal.

Stockpiles can be managed using the [Glitch Harvester](glitch-harvester.md).

Stockpiles can be replayed using the [Stockpile Player](glitch-harvester.md#stockpile-player).

### Memory Domain

_Item that represents a chip or memory pool on an emulated system._

Memory Domains wrap the native memory areas into our own format. Every [Vanguard Implementation](concepts-and-vocabulary.md#vanguard) has to wrap memory areas into Memory Domains, which allows for complete control by RTC. The high-level Memory Domain interface also allows for them to coexist with Virtual Memory Domains, which are a higher level of abstraction on top of normal Memory Domains.

### Virtual Memory Domain

_Item that represents continuous or non-contiguous part(s) of one or many Memory Domains_

Virtual Memory Domains are abstract lists of pointers that act as a Memory Domain. Most of the tools won't know the difference between a normal Memory Domain and a VMD. VMDs are marked with \[V] to show that they are not real. They can be saved and generated from files and formulas. [BlastLayers](concepts-and-vocabulary.md#blastlayer) can also be converted into VMDs.

_More information about Virtual Memory Domains is available in the_ [_VMD Guide_](vmd-generator-advanced.md)_._

### Emulation Step

[Vanguard implementations](concepts-and-vocabulary.md#vanguard) are hooked to their emulator's clock using some sort of CPU loop. This means that RTC's clock is tied the game on a frame basis. Pausing the emulator causes this loop to also get paused, therefore halting any automatic generation of corruption.

### Active and Infinite Units

As of version 5, RTC's [BlastUnit ](concepts-and-vocabulary.md#blastunit)format is completely programmable and is able to faithfully replace every BlastUnit type from the previous versions. Among the available behaviors, Units can be Active, meaning that they will have an effect for a certain amount of time, or Infinite, meaning that the effect will last forever.
