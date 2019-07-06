# Advanced Guide

### Real-Time Corruptor: Advanced Guide

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

## Advanced Guide

### Glitch Harvester

The Glitch Harvester is one of the biggest features of RTC. It is simple to use, yet difficult to master.

_RTC extends emulator savestates into its own format, the StashKey. This allows for corruptions to be attached onto savestates without overwriting the original data._

Basic usage is fairly simple, you create a savestate, select the domains you would like to corrupt, chose an Intensity and click the “Corrupt" button, the emulator then corrupts the selected memory domains and instantly loads the savestate. \(The Glitch Harvester “Corrupt” function can be bound to any key/button\)

### Blast Tools

**Corrupt**

"Corrupt" is the corruption button of the Glitch Harvester. It can corrupt, inject, replay and merge saved items. If _Stash Results_ is selected in the Blast Tools options, it will create a new item in the Stash History box.

![The Glitch Harvester Interface](../../.gitbook/assets/image%20%284%29.png)

**Raw to Stash**

![](../../.gitbook/assets/image%20%282%29.png)

This will create a item in the Stash History box. The generated BlastLayer is applied \(Corruption occurs\) then a new Savestate is created for this item. Active units will be stored in the attached BlastLayer but destructive corruption \(Byte changes\) will be compiled in the Savestate.

### Savestate Manager

**Change -&gt; SAVE/LOAD**

The change button flips the one on its right between SAVE and LOAD. This button toggling system is made this way to prevent accidental overwriting of Glitch Harvester Savestates.

**Reroll Selected**

Rerolls the corruption values of the selected item in the Stash History or Stockpile. This allows to attempt to get better results from a corruption. The result will be sent in the Stash History.

**BlastLayer ON/OFF**

Attempts to uncorrupt/recorrupt the game on the fly. Results not guaranteed.

### Blast Tools options

![](../../.gitbook/assets/image.png)

The Corrupt, Inject and Original options will change the function of the "Corrupt" button.

**Corrupt** is the default setting. Corrupt will have its default behavior and loaded StashKeys will include corruption when replayed.

**Inject** will make the Corrupt button load the corruption layer from the selected item in the Stash History or Stockpile Manager into the currently selected Glitch Harvester Savestate. The same action will happen when clicking on an item in the Stash History or Stockpile Manager.

**Original** will load the selected item from the Stash History or Stockpile Manager without the corruption layer.

### Behaviors

**Auto-Load State** makes it so a Savestate is loaded during Corruption or Replaying and item. When the _Corrupt_ modifier is selected, loading an item from the Stash History or Stockpile Manager will use the embedded Savestate in the StashKey. Otherwise, it comes from the selected item in the Savestate Manager.

**Load on select** causes the StashKey to be loaded when an item is selected from the Stash History or Stockpile Manager. When this option is unchecked, loading a selected item requires to press the Blast/Send button.

**Stash Results** makes it so generated corruption will be added to the Stash History upon generation of a BlastLayer. If a generated BlastLayer has 0 units, the StashKey will not be added to the Stash History.

### Render Output

_**This option is currently only available when RTC is connected to BizHawk**_

![](../../.gitbook/assets/image%20%281%29.png)

This allows you quickly/automatically start audio/video rendering when corrupting using the Glitch Harvester. Rendered files will be saved in the “RENDEROUTPUT” folder which is in _RTCV/RENDEROUTPUT_

**Render type** allows you to select a file format for rendering. If you're getting an error with AVI rendering, it might mean that no codec is selected in BizHawk. In order to do so, you must start an AVI rendering from BizHawk at least once.

**Render at load** will start the render when an item from the Stash History or Stockpile Manager is loaded.

The SAVE and LOAD are for saving and loading Glitch Harvester Savestates.

![](../../.gitbook/assets/190704183858%20%286%29.gif)

**Numeric Buttons**

Numeric buttons are used to select a Glitch Harvester save-state slot.

An associated Textbox can be used for very short descriptions.

**Back and Forward**

This switches between pages of 7 Glitch Harvester Savestates.

**Load state on click**

If checked, the Glitch Harvester will load a save state upon clicking on it.

**Load/Save Savestate List**

These buttons allow you to Save and Load the filled Glitch Harvester Savestates slots to/from a file in a similar format to a Stockpile.

### Intensity

This control is linked to the intensity controls in the Main Window. It multiplies the amount of generated Units on every Blast.

![](../../.gitbook/assets/image%20%283%29.png)

### Stash History

This is where new corruptions are stashed. The items that appear there can be sent to a Stockpile using the "To Stockpile" button. Selecting an item in the list will replay the generated corruption.

### Stockpile Manager

This part of the Glitch Harvester is dedicated to edit and do operations onto Stockpiles.

The **Load** button allows you to either load a Stockpile or load a Settings file from an _SKS_ file.

Using **Save as** and **Save** buttons will generate/overwrite an _SKS_ file that contains corruption data, binaries and savestates. The _SKS_ file can also contains the config file from the last person who saved it. By default, the Glitch Harvester does not include roms and binaries. This behavior can be changed in the Glitch Harvester settings.

**Using someone's config file**

When replaying a stockpile, corruptions can appear different if there are differences in emulator configurations. While RTC is able to detect core mismatches during loading, specific configuration differences are not.

Loading someone's config file pretty much guarantees that your Emulator is in the same state as the person who saved the Stockpile. While your controller config could be lost during the time this config is loaded, it can be reverted afterwards by selecting the **Restore Emulator config Backup** option from the Load menu.

**Import**  
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



![](../../.gitbook/assets/190704190157.gif)

![](../../.gitbook/assets/image%20%285%29.png)

![](../../.gitbook/assets/image%20%288%29.png)

