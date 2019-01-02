# The Blast Editor

The Blast Editor is a tool for manipulating a StashKey in the Glitch Harvester.  This allows the user to edit, add, or remove effects from the BlastLayer.  

![RTC 3.8 Blast Editor](/assets/blast-editor-guide/blast-full-image.png)


### Index

* [**Index**](#index "Self appointed!")
  * [**Purpose**](#purpose)
    * [Sanitize](#Sanitize)
    * [Method](#method)
    * [Editing](#editing)
  * [**Functions**](#functions)
  	* [BlastLayer Info](#blastlayer-info)
  	* [Shift Selected Rows](#shift-selected-rows)
  	* [Disabling](#disabling-functions)
  	* [Searching](#searching)
  	* [Load](#load)
  	* [Apply Corruption](#apply-corruption)
  	* [Send to Stash](#send-to-stash)
  * [**Unit**](#category)
  	* [Lock](#lock)
  	* [Selection](#selection)
  	* [BlastUnit Type](#blastunit-type)
  	* [Source Domain](#source-domain)
  	* [Source Address](#source-address)
  	* [Parameter Domain](#parameter-domain)
  	* [Parameter Value](#parameter-value)
  	* [Notes](#notes)

## Purpose

The purpose of the Blast Editor is to provide the user with the ability to edit the corruptions they create.  At a lower level, users may sanitize their corruptions to remove unnecessary memory writes.  Experienced users may utilize their knowledge of memory to inject specific BlastUnits to obtain their ideal corruption.

#### Sanitize

Sanitizing corruptions is an important habit that should be regularly practiced.  Not only will it remove unnecessary graphical glitches, deafening audio, and clown vomit, but also it will improve the overall stability of the game.  It's no fun if you have a great corruption that can only be played for half a second before the game crashes!

#### Method

The BlastLayer size can vary from just a few Units to several thousand depending on the intensity of the corruption.  

![Small BlastLayer Size](/assets/blast-editor-guide/blast-layer-individual.png)

With a small number of units, the user may individually disable unnecessary memory writes by unchecking them.  

With larger BlastLayer sizes, unchecking individual Units will take too long.  Instead, use the Randomly Disable 50% button to disable half of the BlastLayer.  Repeatedly disable 50% and remove half as long as the corruption persists after loading.

##### Video example

{% youtube %} https://www.youtube.com/watch?v=LwykHjqAIT4 {% endyoutube %}

#### Editing

After a corruption has been reduced to a few Units, their settings can be changed on the fly through the Blast Editor.  Changing options such as the BlastUnit Mode (SET, ADD, SUBTRACT, ETC.), tilting the Source Address, and changing Parameter Values can result in different variations on the corruption.  To change a value, double-click on it and reload the corruption to see the new effect.

## Functions

![Blast Editor Functions](/assets/blast-editor-guide/blast-functions.png)

#### BlastLayer Info

The BlastLayer Info provides information about the current BlastLayer.  The size of the BlastLayer (total Units) is displayed here.

#### Shift Selected Rows

This menu adjusts the selected option (Source Address, Parameter Domain, Parameter Value) through the drop down menu.  The value will be decremented/incremented by the supplied step size.

#### Disabling

###### Randomly Disable 50% 

Disables 50% of the BlastLayer.  Typically used for sanitizing large BlastLayers.

###### Invert Disabled

Turns all selected Units off and all unselected Units on.

###### Disable Everything

Turns all Units off.

###### Enable Everything

Turns all Units on.

#### Searching



#### Load

Pass

#### Apply Corruption

Pass

#### Send to Stash

Pass