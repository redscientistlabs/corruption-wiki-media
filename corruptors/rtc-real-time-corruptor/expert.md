# Expert Guide

#### Real-Time Corruptor: Expert Guide

* [**Index**](expert.md)
  * [**Hotkeys**](expert.md#hotkeys)
  * [**Blast Editor \(Editing BlastLayers\)**](expert.md#blast-editor)
  * [**Virtual Memory Domains**](expert.md#virtual-memory-domains)
    * [Virtual Memory Domain Pool](expert.md#virtual-memory-domain-pool)
    * [Virtual Memory Domain Generator](expert.md#virtual-memory-domain-generator)
  * [**Generating Active Tables**](expert.md#generating-active-tables)
  * [**Development**](expert.md#rtc-dev-discord)

## Expert Guide

### Hotkeys

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

### Blast Editor

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

### Virtual Memory Domains

Virtual Memory Domains, also called VMDs, are virtual representations of areas from one or multiple real Memory Domains. The VMD Generator uses address instructions to make VMD Prototypes which can be used to generate/regenerate VMDs. These prototypes are very lightweight, save/load from a file and can also be created from a Corruption in the Glitch Harvester.

#### Virtual Memory Domain Pool

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

#### Virtual Memory Domain Generator

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



### RTC Dev Discord

If you need advanced help, want to report bugs, ask features or even help with development, we have a development Discord server.

**The rules are the following**

→ Do not spam, post memes or cause trouble.

→ Prioritize big blocks of text over multiple posts \(it makes them easier to delete if needed\)

→ **\#corruption\_general** is for discussing of corruption-related things

→ **\#corruption\_showcase** is for sharing corruptions you made. Please focus on new discoveries and experiments with new features. Don't post SMB1 tileset vomit.

→ **\#corruption\_help** is for requesting help or any kind of support for corruption-related programs, technique and all sorts of issues. Use this channel to discuss about issues before reporting an actual bug.

→ Your requests may get erased and reposted in a stylized box.

→ **Keep your discussion related to RTC and other relevant topics.**

→ **Some of our members have some online notoriety. I will gently ask you stay calm and polite when they are around and refrain from bugging them. Childish fanboyism is not tolerated.**

If you agree to the rules shown above, you can join at the link below

### [I agree. Let me in](https://discord.gg/uzxHvUV)

