# Advanced Guide

### Real-Time Corruptor: Advanced Guide

* **Index**
  * \*\*\*\*[**Glitch Harvester**](advanced.md#glitch-harvester)\*\*\*\*
    * [Blast Tools](advanced.md#blast-tools)
      * [Corrupt button](advanced.md#corrupt-button)
      * [Raw to Stash](advanced.md#raw-to-stash)
      * [Reroll Selected](advanced.md#reroll-selected)
      * [BlastLayer : ON/OFF](advanced.md#blastlayer-on-off)
      * [Blast Tools options](advanced.md#blast-tools-options)
      * [Render Output](advanced.md#render-output)
    * [Savestate Manager](advanced.md#savestate-manager)
    * [Intensity](advanced.md#intensity)
    * [Stash History](advanced.md#stash-history)
    * [Stockpile Manager](advanced.md#savestate-manager)
  * \*\*\*\*[**Stockpile Player**](advanced.md#stockpile-player)\*\*\*\*

## Glitch Harvester

![The Glitch Harvester Interface](../../.gitbook/assets/image%20%2819%29.png)

The Glitch Harvester is one of the biggest features of RTC. It is simple to use, yet difficult to master.

_RTC extends emulator savestates into its own format, the_ [_StashKey_](basic/#stashkey)_. This allows for corruptions to be attached onto savestates without overwriting the original data._

Basic usage is fairly simple, you create a savestate, select the domains you would like to corrupt, chose an Intensity and click the “Corrupt" button, the emulator then corrupts the selected [memory domains](basic/#memory-domain) and instantly loads the savestate. \(The Glitch Harvester “Corrupt” function can be bound to any key/button\)

### Blast Tools

![](../../.gitbook/assets/image%20%2812%29.png)

#### Corrupt button

"Corrupt" is the corruption button of the Glitch Harvester. It can corrupt, inject, replay and merge saved items. If _Stash Results_ is selected in the Blast Tools options, it will create a new item in the [Stash History](advanced.md#stash-history) box.

#### Raw to Stash

This will create a item in the [Stash History](advanced.md#stash-history) box. The generated [BlastLayer ](basic/#blastlayer)is applied \(Corruption occurs\) then a new Savestate is created for this item. Active units will be stored in the attached BlastLayer but destructive corruption \(Byte changes\) will be compiled in the Savestate.

#### Reroll Selected

Rerolls the corruption values of the selected item in the [Stash History](advanced.md#stash-history) or [Stockpile Manager](advanced.md#stockpile-manager). This allows to attempt to get better results from a corruption. The result will be sent in the Stash History.

#### BlastLayer ON/OFF

Attempts to uncorrupt/recorrupt the game on the fly. Results not guaranteed.

### Blast Tools options

![](../../.gitbook/assets/image%20%281%29.png)

The Corrupt, Inject and Original options will change the function of the "Corrupt" button.

**Corrupt** is the default setting. Corrupt will have its default behavior and loaded [StashKeys ](basic/#stashkey)will include corruption when replayed.

**Inject** will make the Corrupt button load the corruption layer from the selected item in the [Stash History](advanced.md#stash-history) or [Stockpile Manager](advanced.md#savestate-manager) into the currently selected Glitch Harvester Savestate. The same action will happen when clicking on an item in the Stash History or Stockpile Manager.

**Original** will load the selected item from the [Stash History](advanced.md#stash-history) or [Stockpile Manager](advanced.md#stockpile-manager) without the corruption layer.

### Behaviors

**Auto-Load State** makes it so a Savestate is loaded during Corruption or Replaying and item. When the _Corrupt_ modifier is selected, loading an item from the Stash History or Stockpile Manager will use the embedded Savestate in the [StashKey](basic/#stashkey). Otherwise, it comes from the selected item in the Savestate Manager.

**Load on select** causes the [StashKey ](basic/#stashkey)to be loaded when an item is selected from the Stash History or Stockpile Manager. When this option is unchecked, loading a selected item requires to press the Blast/Send button.

**Stash Results** makes it so generated corruption will be added to the Stash History upon generation of a BlastLayer. If a generated BlastLayer has 0 units, the [StashKey ](basic/#stashkey)will not be added to the [Stash History](advanced.md#stash-history).

### Render Output

_**This option is currently only available when RTC is connected to BizHawk**_

![](../../.gitbook/assets/image%20%286%29%20%281%29.png)

This allows you quickly/automatically start audio/video rendering when corrupting using the Glitch Harvester. Rendered files will be saved in the “RENDEROUTPUT” folder which is in _RTCV/RENDEROUTPUT_

**Render type** allows you to select a file format for rendering. If you're getting an error with AVI rendering, it might mean that no codec is selected in BizHawk. In order to do so, you must start an AVI rendering from BizHawk at least once.

**Render at load** will start the render when an item from the [Stash History](advanced.md#stash-history) or [Stockpile Manager](advanced.md#stockpile-manager) is loaded.

### Savestate Manager

![](../../.gitbook/assets/190704183858%20%286%29.gif)

**Change -&gt; SAVE/LOAD**

The change button flips the one on its right between SAVE and LOAD. This button toggling system is made this way to prevent accidental overwriting of Glitch Harvester Savestates.

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

![](../../.gitbook/assets/image%20%2818%29.png)

This control is linked to the [intensity ](basic/#intensity)controls in the Main Window. It multiplies the amount of generated Units on every Blast.

### Stash History

![](../../.gitbook/assets/190704190157.gif)

This is where new corruptions are stashed. The items that appear there can be sent to a Stockpile using the "To Stockpile" button. Selecting an item in the list will replay the generated corruption.

### Stockpile Manager

![](../../.gitbook/assets/image%20%2822%29.png)

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

## Stockpile Player

![](../../.gitbook/assets/image%20%2847%29%20%281%29.png)

This is a minimalist version of the Glitch Harvester's [Stockpile Manager](advanced.md#stockpile-manager). It allows you to load [Stockpiles](basic/#stockpile) and replay corruptions.

The Previous and Next buttons are for jumping from a corruption to another. They do the same thing as clicking on the corruptions directly.

The Red refresh button replays the current corruption.

BlastLayer Button: Toggles ON/OFF the BlastLayer of the last executed StashKey, essentially attempting to uncorrupt/recorrupt in real-time.

If the button in the Note column has a ⚠ Symbol, it means that a note is attached to the corruption. Click on it to open the note.

Various options from RTC's [Engine Config](basic/#corruption-engines) menu are present in a contextual menu if you right-click on corruptions.



