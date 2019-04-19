# Advanced Guide

#### Real-Time Corruptor: Advanced Guide

* [**Index**](advanced.md#advanced-guide)
  * [**Glitch Harvester**](advanced.md#glitch-harvester)
    * [Action Panel](advanced.md#action-panel)
    * [Savestate Manager](advanced.md#savestate-manager)
    * [Intensity](advanced.md#intensity)
    * [Action Modifiers](advanced.md#action-modifiers)
    * [Action Triggers](advanced.md#action-triggers)
    * [BlastLayer Toggle](advanced.md#blastlayer-toggle)
    * [Reroll Selected](advanced.md#reroll-selected)
    * [Render Output](advanced.md#render-output)
    * [Stash History](advanced.md#stash-history)
    * [Stockpile Manager](advanced.md#stockpile-manager)
  * [**Stockpile Player**](advanced.md#stockpile-player)
  * [**RTC Multiplayer**](advanced.md#rtc-multiplayer)
    * [Connecting RTCs together](advanced.md#connecting-rtcs-together)
    * [Metagames and Multiplayer Features](advanced.md#metagames-and-multiplayer-features)

## Advanced Guide

### Glitch Harvester

The Glitch Harvester is one of the biggest features of RTC. It is simple to use, yet difficult to master.

Basic usage is fairly simple, you create a savestate, select the zones you would like to corrupt, chose an intensity and click the “Blast/Send” button, the emulator then corrupts the selected memory zones and instantly loads the savestate. \(The “Blast/Send” function can be bound to any key/button\)

#### The interface

_This will explain the complex layout of interactive elements which makes the interface._

\[INSERT GLITCH HARVESTER SCREENSHOT WITH CLICKABLE AREAS\]

#### Action Panel

**Blast/Send**

Blast/Send is the corruption button of the Glitch Harvester. It can corrupt, inject, replay and merge saved items. If _Stash Results_ is checked, it will create a new item in the Stash History box.

**Send Raw to Stash**

This will create a item in the Stash History box. The generated BlastLayer is applied \(Corruption occurs\) then a new Savestate is created for this item. Alterating corruption \(Cheats and Pipes\) will be stored in the attached BlastLayer but destructive corruption \(Byte changes\) will be compiled in the Savestate.

#### Savestate Manager

**Change -&gt; SAVE/LOAD**

The change button flips the one on its right between SAVE and LOAD. This button toggling system is made this way to prevent accidental overwriting of Glitch Harvester Savestates.

The SAVE and LOAD are for saving and loading Glitch Harvester Savestates.

**Numeric Buttons**

Numeric buttons \(1-40\) are used to select a Glitch Harvester save-state slot.

An associated Textbox can be used for very short descriptions.

**Back and Forward**

This switches between pages of 10 Glitch Harvester Savestates.

**Load on click**

If checked, the Glitch Harvester will load a save state upon clicking on it.

**Load/Save Savestate List**

These buttons allow you to Save and Load the 40 Glitch Harvester Savestate slot to/from a file in a similar format to a Stockpile.

#### Intensity

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

**BlastLayer Toggle**

Attempts to uncorrupt/recorrupt the game on the fly. Results not guaranteed.

**Reroll Selected**

Rerolls the corruption values of the selected item in the Stash History or Stockpile. This allows to attempt to get better results from a corruption. The result will be sent in the Stash History.

#### Render Output

This allows you quickly/automatically start audio/video rendering when corrupting using the Glitch Harvester. Rendered files will be saved in the “RENDEROUTPUT” folder which is in _BizHawk/RTC/RENDEROUTPUT_

**Render type** allows you to select a file format for rendering. If you're getting an error with AVI rendering, it might mean that no codec is selected in BizHawk. In order to do so, you must start an AVI rendering from BizHawk at least once.

**Render at load** will start the render when an item from the Stash History or Stockpile Manager is loaded.

#### Stash History

This is where new corruptions are stashed. The items that appear there can be sent to a Stockpile using the button between the Stash History and Stockpile Manager.

#### Stockpile Manager

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

### Stockpile Player

This is a minimalist version of the Glitch Harvester's Stockpile Manager. It allows you to load Stockpiles and replay corruptions.

The Previous and Next buttons are for jumping from a corruption to another. They do the same thing as clicking on the corruptions directly.

The Red refresh button replays the current corruption.

BlastLayer Button: Toggles ON/OFF the BlastLayer of the last executed StashKey, essentially attempting to uncorrupt/recorrupt in real-time.

If the button in the Note column has a ⚠ Symbol, it means that a note is attached to the corruption. Click on it to open the note.

Various options from RTC's Engine Config menu are present in a contextual menu if you right-click on corruptions.

### RTC Multiplayer

#### Connecting RTCs together

Before connecting RTCs together, let this small fact known : RTC's Detached mode uses the same components as the Multiplayer mode in RTC. This is why you must run RTC in Attached mode in order to connect RTCs together.

 **Session Settings** 

RTC uses TCP port 42069 by default. You will need to open this port in your router if you plan on being the server. The client doesn't need it.

Simply start the multiplayer in the right category on order to start the server or connect to it.

You can also run TWO RTCs in Multiplayer on the same machine by connecting to "127.0.0.1" or simply leaving the case blank.

RTC's Multiplayer is fully bidirectional, meaning that both Client/Server can do exactly the same thing.

 **Manual Commands** 

There are 3 types of commands: PUSH : Sends an item to the other RTC PULL : Downloads an item from the other RTC SWAP : Swaps items between the two RTCs

Command items Game: Game ROM State: Game's State Screen: Picture of RTC's game's screen BlastLayer: Last executed Corruption's Blast StashKey: Last executed Corruption Item

 **Video Streaming** 

The Multiplayer screen and Stream options are for streaming a video feed between RTCs.

The screen can be popped out of the RTC Multiplayer options.

#### Metagames and Multiplayer Features

 **Game of Swap** 

Both video streams will start. A red bar will start shrinking until it totally disappears. Once the red bar is gone, the two currently running games will be exchanged between RTCs.

 **BlastBoard** 

This is like a Soundboard, except that instead of sounds, it's Blasting the other RTC using the BlastLayers of the currently loaded Stockpile. You may wanna sanitize your corruptions using the Blast Editor before using this mode.

 **Splitscreen** 

This pops out the Multiplayer screen and attaches both Bizhawk feeds together in a new window.

This hides the default Bizhawk window so you'll want to stop Splitscreen before closing BizHawk.

