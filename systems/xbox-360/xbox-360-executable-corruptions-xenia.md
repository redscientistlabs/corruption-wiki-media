---
description: by Snuffles
---

# Xbox 360 Executable Corruptions (Xenia)

using Xenia and FileStub

This guide explains how to get Xbox 360 corruptions working using FileStub and Xenia. This method allows for Xbox 360 corruptions, but ultimately it is a slow and tedious process due to the lack of savestates.

**This guide presupposes that the game is already operational on the emulator. If you haven't gotten your game to run in Xenia, stop reading this guide and figure this one out.**

## **Dumping the Files on Stock**

The Xenia quickstart guide has a great guide to dumping your own games on stock consoles. [https://github.com/xenia-project/xenia/wiki/Quickstart#how-to-rip-games](https://github.com/xenia-project/xenia/wiki/Quickstart#how-to-rip-games)

## **Extracting the Files**

### **GOD/Games on Demand** <a href="#pu7wuyogtrfs" id="pu7wuyogtrfs"></a>

After you have dumped the games you want to corrupt you need to extract the files to get the XEX. You’re going to want to download a program called “god2iso” in order to convert the file into iso format. You can get it from here: [God2ISO - Xbox 360 Games on Demand to CD Image Converter | Digiex](https://digiex.net/threads/god2iso-xbox-360-games-on-demand-to-cd-image-converter.7115/#google\_vignette). Launch the “God2Iso.exe” file from the downloaded program and add a GOD package from your USB drive. Choose an output directory and press the “Go!” button.

![](<../../.gitbook/assets/0 (1).png>)

After it is done you will find an iso that has the same name as the GOD package you added. Now you need to download a program called “isoextract” which you can get from here: [Xbox 360 XISO Extract - BEST an easiest XDG3 extraction tool, with GUI + FTP. | Digiex](https://digiex.net/threads/xbox-360-xiso-extract-best-an-easiest-xdg3-extraction-tool-with-gui-ftp.9711/). Launch the “XBOX360 ISO Extract.exe” file from the downloaded program. Choose the ISO folder and the destination for the extracted files to go. After you are done choosing, press the “go” button.

![](<../../.gitbook/assets/1 (1).png>)

You should now have the files of the game you want to corrupt.

### **XBLA/Xbox Live Arcade** <a href="#m7k7reuidmhz" id="m7k7reuidmhz"></a>

After you have dumped the games you want to corrupt you need to extract the files to get the XEX. You’re going to want to download a program called “wxPirs” in order to extract the files of the XBLA title. You can get it from here: [Wxpirs - extract content from Xbox 360 Demos, Video DLC and Arcade game containers | Digiex](https://digiex.net/threads/wxpirs-extract-content-from-xbox-360-demos-video-dlc-and-arcade-game-containers.9464/#google\_vignette). Launch the “wxPirs.exe” file from the program you downloaded. Click open file in the program and go to the folder where the XBLA title file is. Extract all the files somewhere on your hard drive.

![](<../../.gitbook/assets/2 (1).png>)

You should now have the files of the game you want to corrupt.

## **Decompressing and Unencrypting the XEX**

You should have a “default.xex” file in the root folder of the game you extracted. This file needs to be decompressed and unencrypted before being able to be corrupted. In order to do this, you’re going to need a tool called “XexTool”, which you can get here: [XEXTool 6.3 Download | Digiex](https://digiex.net/threads/xextool-6-3-download.9523/). Alternatively, if you prefer to use a GUI tool, you can use a program called “Xbox 360 Game Hack”, which you can download here: [Xbox 360 Game Hack 6.3 - Patch Xbox 360 .xex files (patch region, media, kinect) | Digiex](https://digiex.net/threads/xbox-360-game-hack-6-3-patch-xbox-360-xex-files-patch-region-media-kinect.7430/#post38498), although note that this guide will be using the command line tool. Copy over the default.xex file to the folder where “xextool.exe” is stored.

![](<../../.gitbook/assets/3 (1).png>)

This is what the XexTool folder should look like when preparing to decompress and unencrypt.

In file explorer, there is a bar to the left of the search bar that shows the path to the current directory you’re in (should be the XexTool folder). Click the empty space in that bar,

![](<../../.gitbook/assets/4 (1).png>)

The red arrows point to the empty space.

type “cmd”

![](<../../.gitbook/assets/5 (1).png>)

and press enter. Command prompt should now open. To keep things simple, just type in “xextool -c u -e u -o default2.xex default.xex” without the quotes.“default2.xex” can be whatever you want. Copy the “default2.xex” file to the root of the extracted game folder. The unmodified default.xex should be there alongside your newly decompressed and unencrypted default2.xex file.

## **Corrupting and Loading**

Open the RTC launcher and download Dolphin. Download FileStub if you haven’t already and open it. Click the settings icon in the top right corner of FileStub and turn Big Endian on. Add the modified default2.xex into FileStub. Click load targets into RTCV.

![This is what FileStub should look like when you load targets in RTCV.](<../../.gitbook/assets/6 (1).png>)

Change the blast radius to normalized and the corruption engine to vector. Click the “My Lists” button and then click “Import List File”. Go to your RTC folder and go into VERSIONS -> RTCV\_(version) -> Dolphin -> LISTS and import all of the lists in this folder.

![](<../../.gitbook/assets/7 (1).png>)

Go back to engine config and click on the “Package Downloader” button. Go to LISTS and download the following lists: [DolphinFloatInstructions\_by\_NullShock78.pkg](http://cc.r5x.cc/rtc/packages/CATALOG\_3/LISTS/DolphinFloatInstructions\_by\_NullShock78.pkg) and [DolphinFloatPassthrough\_by\_NullShock78.pkg](http://cc.r5x.cc/rtc/packages/CATALOG\_3/LISTS/DolphinFloatPassthrough\_by\_NullShock78.pkg).

![](<../../.gitbook/assets/8 (1).png>)

Go back to “My Lists” and click “Refresh List Files”. Go back to engine config. The new list files should be there now. Now it’s finally time to do your first test corruption. For the limiter, set the list to be \_Dolphin\_PT\_FLT\_MATH and set the value to be the same. This is a great beginning combo.

![Here’s what your first setup should look like.](<../../.gitbook/assets/9 (1).png>)

The guide will detail other list combinations later. Open up the Glitch Harvester. You’re going to want to go for a layer size of around 100.

<figure><img src="../../.gitbook/assets/layer size.PNG" alt=""><figcaption></figcaption></figure>

Too little and you’re not going to see much broken stuff, too much and all you’ll see is bars stretched across your screen. The amount of blast units you’ll get depends on the lists you use and the XEX size. If you’re getting way too many or way too little, make sure you have Big Endian set in FileStub or didn’t accidentally increase the alignment past 0. After you have corrupted the file, drag and drop the “default2.xex” into Xenia to load the corrupted XEX. Alternatively you can set the target execution in the FileStub advanced settings to open Xenia every time you corrupt the file.

## **List Combinations and Info**

Here are some of the lists and combinations that have been tested and work well. If a list is not listed here, that probably means it should be avoided unless you know what you are doing.\
Guide: (limiter) -> (value)

\_Dolphin\_PT\_FLT\_MATH -> \_Dolphin\_PT\_FLT\_MATH\
This is what you should use if you’re just beginning, it is the least crashy out of everything that will be here but it is not completely crash proof.

\_Dolphin\_FLT\_DBL\_GIGA -> \_Dolphin\_FLT\_DBL\_GIGA\
Medium crashiness. Gives various unique results when compared to other things on here.

\_Dolphin\_FLT\_DBL\_MATH -> \_Dolphin\_FLT\_DBL\_MATH\
Medium crashiness. Gives less results than \_Dolphin\_FLT\_DBL\_GIGA.

\_Dolphin\_FLT\_LOAD -> \_Dolphin\_NOP\
Most crashy. One of the most difficult ones there are here while still at least semi-consistently being able to get results. Requires lower intensity than others to not get crashes.

\_Dolphin\_FLT\_STORE -> \_Dolphin\_NOP\
Most crashy. One of the most difficult ones there are here while still at least semi-consistently being able to get results. Requires lower intensity than others to not get crashes.

\_Dolphin\_FMR -> \_Dolphin\_NOP\
Not all that crashy, but results mostly consist of unplayable and unwatchable screen warping. Results and success very much vary per game. Requires high intensity to get even remotely anything. Provides the most unique effects out of anything here when you aren’t looking at an enlarged concrete texture covering your entire screen.

## **Potential Weird Scenarios**

Sometimes, it’s not as simple as decompressing and decrypting the default.xex and corrupting it. There may be some scenarios where you need to do more.

### **Corrupting Games With Title Updates** <a href="#id-5itjnbrehr54" id="id-5itjnbrehr54"></a>

You should generally avoid trying to use Title Updates while corrupting games. Applying the Title Update while also corrupting is highly inconvenient and unnecessary for most games as most are only bug fixes. There are some games however, with massive amounts of Title Updates that make the game what it is (Minecraft, Terraria etc.) If you insist on corrupting games with Title Updates, you will need to obtain the Title Update. This guide will not go over how to obtain it. After you have obtained the Title Update, you will need to install it into Xenia. In order to do this you just need to click File -> Install Content and then install the Title Update file. Go to the content folder in Xenia, you will find the Title ID of the game you installed the Title Update for. Navigate that folder until you find a folder containing a “default.xexp” file.

![](<../../.gitbook/assets/10 (1).png>)

Copy all of the files in the Title Update into the folder with your base game (if it overwrites files don’t worry about it). You will notice how there is now a “default.xexp” file next to the normal default.xex file. This is the patch file for the default.xex file. Copy over both files to the xextool folder.

![This is what the XexTool folder should look like.](<../../.gitbook/assets/11 (1).png>)

To patch it, type in the following command: “xextool -p default.xexp default.xex” without quotation marks. After you do that you’re going to need to fix it so it doesn’t need a separate patch file. To do that type “xextool -u default.xex”. Then, you’re going to want to remove all XEX limitations. To do that type “xextool -r a default.xex”. Finally, after all that you can decompress and unencrypt the XEX file. Remember, you can do that by typing “xextool -c u -e u -o default2.xex default.xex”. After all of that you can finally corrupt the newly patched XEX file and drag and drop it into Xenia.

### **Corrupting Games With “DLL” Files** <a href="#id-7f6zf7dfad3y" id="id-7f6zf7dfad3y"></a>

There is this weird case scenario with Valve games on the Xbox 360 (and Terraria with no Title Update) where there are “DLL” files (they’re just XEX files disguised as a DLL file) running alongside the normal default.xex. Valve games are currently the only known games that are like this, but there are more than likely other games on the Xbox 360 that are like this that this guide would help with. To tell if you should be corrupting the “DLL” files and not the default.xex, look at the size of the default.xex compared to the “DLL” files. If the default.xex doesn’t even reach the megabyte range, the “DLL” files are more than likely the files you want to corrupt. In order to corrupt these types of games, you need to decompress and decrypt the “DLL” files like any normal XEX file. You don’t even want to touch the default.xex as it will cause the game to crash on boot when loading a modified one. For this guide, we will be using the game “Portal: Still Alive”. The common “DLL” files you want to corrupt are “engine\_360.dll”, “vphysics\_360.dll”, “MaterialSystem\_360.dll”, “shaderapidx9\_360.dll” and “stdshader\_dx9\_360.dll”. You can corrupt the other “DLL” files if you want. Decompress and decrypt those files, but you may want to decompress all the “DLL” files just in case you want to have those at the ready.

![](<../../.gitbook/assets/12 (1).png>)

![Being able to have all “DLL” files at the ready to corrupt is very useful.](<../../.gitbook/assets/13 (1).png>)

After you decompress and decrypt the “DLL” files, you will need to straight up replace the unmodified “DLL” files with the modified ones. Therefore, it is impossible to do the method of creating multiple copies of the files in order to decrease the downtime of corruptions. After you have replaced all of the “DLL” files of the game on the USB drive, you will need to add all of the “DLL” files into RTC.

![](<../../.gitbook/assets/14 (1).png>)

The corruption settings you should use are like before except for a few things. Instead of using a normalized blast radius, you’ll want to use a spread or even blast radius. You’ll also want to have a layer size of around 80 if you’re only corrupting the common “DLL” files mentioned earlier as the game is a lot more sensitive than most. This may not be the case for other games. You may want to try to get a bigger layer size if you are corrupting more of them. After you are done corrupting the files just drag and drop the normal default.xex into Xenia.

## **Notes**

You will find that XBLA games are in trial mode. In order to solve this you will need to change the “license\_mask” setting in the “xenia-(master/canary).config.toml” file to 1 or -1.

You need to download Dolphin as the \_Dolphin\_NOP list is only accessible if Dolphin Vanguard is downloaded.

The \_Dolphin\_PT\_FLT\_MATH, \_Dolphin\_PT\_FLT\_ADD, \_Dolphin\_PT\_FLT\_SUB and \_Dolphin\_PT\_FLT\_DIV lists can be mixed around (MATH is the only one that can be used against itself though). For example, Use \_Dolphin\_PT\_FLT\_ADD with \_Dolphin\_PT\_FLT\_SUB to turn addition floats into subtraction floats.

Sanitization is possible but not recommended due to the lack of savestates.

With how unique the Xbox 360 can be with what developers can do with it there may be some extra weird scenarios that may not be mentioned in this guide. We don’t own everything/can’t test everything so if you find something odd that prevents your corrupting experience please join the RTC Discord so we can help solve issues and add solutions to the Wiki.
