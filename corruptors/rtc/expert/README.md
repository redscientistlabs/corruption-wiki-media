# Expert Guide

### Real-Time Corruptor: Expert Guide

* **Index**
  * [**Hotkeys**](./#hotkeys)
  * [**Blast Editor (Editing BlastLayers)**](./#blast-editor)
  * [**Virtual Memory Domains**](./#virtual-memory-domains)
    * [VMD Pool](./#vmd-pool)
    * [VMD Generator](./#vmd-generator)
  * [**Blast Editor Guide**](blast-editor.md)****
  * ****[**Blast Generator Guide**](blast-generator.md)****
  * ****[**VMD Generator Guide**](vmd-generator.md)****
  * ****[**Active Table Guide**](active-table-guide.md)****
  * ****[**Custom Engine Guide**](custom-engine.md)****
  * ****[**Cluster Engine Guide**](../../../rtcv/rtc/expert/cluster-engine-guide.md)****

## Hotkeys

![As of version 5, RTC has its own hotkeys in the Settings and tools menu](<../../../.gitbook/assets/image (9).png>)

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

**Induce KS Crash**

Kills the KillSwitch heartbeat, causing (if enabled) RTC to detect a crash.

**BlastLayer Toggle**

Toggles ON/OFF the BlastLayer of the last executed StashKey

**BlastLayer Re-Blast**

Re-executes BlastLayer of the last executed StashKey.

**Game Protect Back**

Triggers the Back button on Game Protection (If available)

**Game Protect Now**

Triggers the Now button on Game Protection (If available)

![](<../../../.gitbook/assets/image (33) (1).png>)

**Load and Corrupt**

Loads the selected GH SaveState, creates a StashKey in the Stash History and then runs it.

**Just Corrupt**

Creates a StashKey in the Stash History and then runs it without loading a save.

**Reroll**

Triggers the Glitch Harvester's Reroll Selected button

**Load**

Loads the currently selected Glitch Harvester Savestate Box.

**Save**

Saves the game state in the currently Glitch Harvester Savestate Box.

**Stash->Stockpile**

Sends the currently selected item in the Stash History and sends it to the Stockpile.

**Blast+RawStash**

Does a Manual Blast to the game then creates a Raw Stashkey in the Stash History.

**Send Raw to Stash**

Creates a Raw StashKey in the StashHistory

![The Blast Editor hotkeys correspond directly to their buttons](<../../../.gitbook/assets/image (20).png>)

## Blast Editor

![](<../../../.gitbook/assets/image (32).png>)

Any [StashKey ](../basic/#stashkey)in the [Glitch Harvester](../advanced.md#glitch-harvester) can be opened in the Blast Editor by right-clicking on it and select _"Open Selected Item in Blast Editor"_.

Read the [Blast Editor Guide](blast-editor.md) for a detailed explanation of how the Blast Editor works.

## Virtual Memory Domains

![](<../../../.gitbook/assets/image (11).png>)

[Virtual Memory Domains](../basic/#virtual-memory-domain), also called VMDs, are virtual representations of areas from one or multiple real Memory Domains. The VMD Generator uses address instructions to make VMD Prototypes which can be used to generate/regenerate VMDs. These prototypes are very lightweight, save/load from a file and can also be created from a Corruption in the Glitch Harvester.

## VMD Pool

![](<../../../.gitbook/assets/image (27).png>)

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

## VMD Generator

![](<../../../.gitbook/assets/image (14).png>)

An in-depth [VMD Generator Guide](vmd-generator.md) is also available

**Load Domains**

Loads the Memory Domains of the currently active emulation core into the VMD Generator.

**Memory Domain**

This Selector Box allows you to chose a target Domain.

**Domain Size**

The size of the selected Memory Domain in bytes

**Word Size**

The size of a [word](https://en.wikipedia.org/wiki/Word\_\(computer\_architecture\)) for the currently selected memory domain

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

