---
description: For general use with files, directories, and more.
---

# Corrupting Files with FileStub

**Guide written by:** Mistsofnowh3r3\
**Software used in guide:** RTCV, FileStub\


## Assumptions

This guide will assume the following things:

You know the basics of using RTC.

You understand basic RTC terminology.

## Forewarning&#x20;

Do not ever corrupt a file you are not prepared to lose.&#x20;

While FileStub has safeties in place to restore files, it is better to act as if corrupting a file would leave it permanently corrupted. This means it is good to make backups of what you will be corrupting prior to corrupting them.

Do not upload corrupt media directly to Discord or similar.

It is unlikely, but possible, that when trying to display a corrupt image, audio, or video file Discord could freak out and crash for anyone that tries to view the media. So for this reason it is better to externally capture the corrupt media using something like OBS or the Snipping Tool.

Another reason to externally capture the media is that it will likely be displayed differently in different applications, so externally capturing it is better.

## Basic Layout

![](https://lh6.googleusercontent.com/lkHthbYVQsxHPuo6-iTCcb9d\_9pBYZGG\_a31TPcCPP6wzeJxbkLZ7jDLtoPK6NwH0BY4jQPISyFsNuo6CQuBQEi2oBNx\_iPkdLiPftiSgFgVMog2gnHQiugZmFXOUImuACxweSzTJSt8kESY4RRwIA4)



### Left side

#### Status

Shows info on the currently loaded target(s)

### Session

**Restore Targets**

Restores a backup of the file(s) currently loaded into RTCV from the Vault.

**Reset Backups**

Creates a new backup from the current state of the file(s) currently loaded into RTCV. If they are currently corrupt, you will lose the original backup.

### Vault Data

Shows how many files are currently corrupt or “dirty”.

#### Restore All Dirty

Restores all backups in the Vault. This includes backups of things from previous sessions which are not currently loaded as targets.&#x20;

#### Bake All Dirty

Bakes the corruptions of all dirty files. Currently, clicking this will automatically permanently corrupt all currently dirty files with no warning.

#### Clear Vault Data

Clears all data in the Vault and unloads all targets. Cannot be done if any files are dirty

### Top

#### Install Templates from Package Downloader

Opens the Package Downloader.

#### Advanced Options

Expands the view to show extra options. Will go over below.

### ⚙️Cog

**Big endian**

Likely unneeded. Sets the endianness in cases where that is needed.

**Auto-Uncorrupt**

When enabled, reloading a backup performs an uncorruption on the corrupted files instead of copying the file from the Vault. This has a minimal effect when working with small files, but speeds up the backup restoration process as the files get larger.\


**Use Caching + Multithreading**&#x20;

When on, current loaded targets are cached in RAM. Turning off makes the program slower, but is recommended when targeting files larger than the amount of RAM available on your device.

## Target Type

#### Single File

Allows only one file to be selected and corrupted.

#### Multiple files (One domain)

Allows multiple files to be selected and corrupted. All files are added to a memory blob and are laid out one after another, this blob is then represented as a single domain in RTC.

#### Multiple files (Many domains)

Allows multiple files to be selected and corrupted, gives each file a separate Domain.

#### Multiple files (Many domains + Full path)

The same as Multiple files (Many domains) but file path is shown in the domain list. Useful if you're targeting multiple files with the same name.

\


Installed Templates will also show up under this menu.

\


## Target Loading

This is where you select what you will be corrupting.

#### Target List

Unlabeled in the program, but this shows a list of all the files you have currently selected.

#### Browse Target

Browse Target opens a file dialog allowing you to pick which file(s) you will be corrupting.

If any of the Multiple Files are selected as the Target Type this will open a separate file picker which I will explain below.

#### Quick Load drag and drop zone

Automatically selects and loads files you drag and drop here into RTCV&#x20;

#### Set base dir

Theoretically, all files in the selected folder will be added to the Vault backup. Considered unfinished and should not be used.

#### Load targets into RTCV

Loads all targets in the list into RTCV. This button becomes the Unload button afterwards and will unload all targets from RTC.

#### Clear targets

Removes all targets from the list

## Multiple Files Select Dialog

![](https://lh3.googleusercontent.com/3m1L\_jCr06ftwC1oiqvZUFmfyfe-61VI7zkkAPLJPUxGqxiwX5wHCfNieNGUxviG5\_8MDp4ruI3DBxLb5nJ5vC7Jx2F2IMRiaVw\_q1xcY\_6ru4Jw6584-vp1quduXH4OhEnDRodpGKq8yJwuWh7PV2U)

#### File Selection List

Unlabeled in the program, but this shows a list of all the files you have currently selected.

#### Add

Opens another separate file dialog to select a file to add to the File Selection List.

#### Add Folder

Open another different file dialog, choose a folder and add all the files contained in it to the File Selection List. Adds files from all sub folders in the selected folder as well.

#### Remove Selected

Remove the highlighted file from the File Selection List.

#### Clear

Clears all files from the File Selection List.

#### Save list to File

Saves the current File Selection List to a .txt in a location of your choice. This .txt will contain the file path of all the files in the File Selection List.

#### Load list from File

Opens a file dialog to select a previously saved List.

#### Cancel

Closes the Multiple Files Select Dialog.

#### Load Multiple Files in FileStub

Loads all files in the File Selection List into FileStubs Target List.

#### Ignore loading errors

Suppresses error messages when loading files. Useful if you are loading a folder that contains multiple files that otherwise would display an error when trying to load

## Advanced Layout

![](https://lh3.googleusercontent.com/F5stPU\_RGkVZYAYbc8KyqujMbA1sPNt8FuSufdqW6ajfRTomkRyMYfu1nKI7ZNYAkbkKeSZh2PcNl4sWRkrmaGieerorsn-87Vz37\_O5T1rhqSknpKLDcsUDtH5AU7JsbwiA\_hc0u02cNXU7I6XPejY)

### Loaded target information

Shows info on the currently loaded target(s).

### Target execution

Depending on the selection, the options “Edit Exec”, “Kill Process”, and “args” will be shown

#### No execution&#x20;

Nothing is executed upon corruption of target. No options shown.

#### Execute corrupted file

Will attempt to execute the targeted file upon corruption.&#x20;

“Edit Exec” is shown in error and has no effect.

“Kill Process” listed but has no effect\


**Execute with**

Will attempt to execute the targeted file with a selected program upon corruption.&#x20;

“Edit Exec” allows you to choose which program to attempt to execute with.&#x20;

“Kill Process” kills the selected program when it is running.

#### Execute other program

Will execute the selected program upon corruption of target.

“Edit Exec” allows you to choose which program to execute.&#x20;

“Kill Process” kills the selected program when it is running.

“Args” adds arguments to be added to the selected program upon execution.

#### Script

Unimplemented.

### Selected Target settings

#### Header padding & Footer padding

Set the length in bytes of padding of each for the currently highlighted target. Each Target can have its own header and footer offset. This will be explained in Concepts.

#### Save target padding

Saves the inputted paddings to the Vault

### Global Target settings

Unimplemented.

## The RTC window

RTC will be much the same as it usually is with only a few key differences:

There is no button to Auto-Corrupt.

The Savestate Manager in Glitch Harvester is blanked out.

The Manual Blast button is replaced with a Corrupt button which is linked to the Glitch Harvester corrupt button. This works the same as the Glitch Harvester corrupt button and will add items to the Stash.

## Closing FileStub

When FileStub is being closed it will check if there are any dirty files in the vault. If there are, FileStub will warn you that there are dirty files and ask you if you would like to restore them or not.

\


If there are dirty files in the Vault when the program is closed and this message is not shown either due to a crash or something similar. The Vault should still be able to restore any dirty files the next time that FileStub is reopened.

## Concepts&#x20;

### The Vault

The Vault is a system used to create virtual ROMs which can hold entire file structures in them. This is useful for creating Stockpiles. A new Vault copy is created when saving a Stockpile.

### Templates

Templates make corrupting certain things easier. Each template has different options and settings and I will not be going over them in this guide. These act similarly to RTC Plugins and are created in a similar way. Due to this, typical users will not be able to create or edit these.

### Session

A session is everything that happens between loading a target(s) into RTC and unloading that target(s) from RTC.

### File structure

#### Simple File Structure&#x20;

![](https://lh3.googleusercontent.com/Aq-riFGt3Tmx3W8oVepAYO6ofwwopQ19ArsI3yJIwkzeiv\_My4ApNPuJr2U-rvq5zHwqg2lWw3o\_2zTDyTkWUcE\_h8XICkWwjFtCgPjZaYWe551x6jvBxjmOOq-PnU-dzAEGL9lGB9xMRhjRPQ0\_FPE)

Above is a simple example of a file’s structure.

#### Header

The header stores information about the file such as: the file type, the file size, and many other things. Because of this, corrupting the header will usually cause the file to become unreadable even if none of the data is corrupt.

#### Data

The data, in most cases, is what we actually want to corrupt.

#### Footer

The footer, like the header, contains info on the file. It will also contain a section to mark the end of a file.

### Realistic File Structure

![](https://lh6.googleusercontent.com/joPAyiLenaDhQtEXKoEs2sXqWaLgXkfo2dDesfHGs28dFjl86MOLzqwrTgSnl2z-ww\_lx-QNoBMsClnS2nqRLHSP-RAUiaDLss8woaj87Dl2pztuZVnKYBLtBJbu19F6GvDMagJ2lr1AhZqQBbzuH84)

Above is a more realistic depiction of a file structure, we will use it for learning purposes, but it should not be referenced for usage.

Here’s a more realistic depiction of a file’s structure. The footer and header have been rendered with more detail. Still, the only thing we want to touch is the data. So, In this example, the header should be set to 28 and the footer to 20.

## A note on stockpile creation

It is not recommended to use header and footer padding when creating a stockpile is the goal. Anyone else who would open the stockpile would have to have their header and footer settings exactly the same as you do to get the same results.

\
\
