---
description: Startup guide on how to run RTC on Linux using Wine
---

# Running RTCV on Linux

  
__**Guide written by:** __LuckyLuigiX4  
__**Linux distro used in the making of this guide:** Linux Manjaro__

**If you are a Windows user, you do not need to follow this as RTC is already made for Windows**

## **What is Wine?**

In Layman’s terms, it’s a Linux Program that allows Windows only programs to run on Linux. It’s gotten very good the past few years and can now run RTCV.

### **How to Run RTCV under Wine:**

This will be a step by step guide on how to run RTCV under Wine. Pictures will be shown.

This Guide will assume you already have RTCV Downloaded to your system and Wine Installed, it’s a quick good search if you somehow don’t have it.

**1. Install Lutris**

Lutris is a great Linux application that allows for easy Management of games and programs that you need to run under wine.

The Lutris Website shows how to install on many Distributions [https://lutris.net/downloads/](https://lutris.net/downloads/)

\(If you know what you are doing then you may not need to use Lutris, but it’s highly reccomended\)

**2. Open Lutris and Add a Game**

![](../../.gitbook/assets/image%20%2851%29.png)

Once you’ve opened Lutris, You’re going to want to add a new game.

**3. Enter Name and Select a Runner**

In the “Game Info” Tab, Enter a Name for the Program \(Ex: RTCV\) and select “Wine” from the Runner’s List

![](../../.gitbook/assets/image%20%2852%29.png)

![](../../.gitbook/assets/image%20%2857%29.png)

**3.5 Extract RTCV to a folder**

You most likely want to create a folder for Wine Programs for Lutris if you plan on using it in the future. Make a folder called wine and make folders inside that for individual Programs.

**4. Enter the Executable Path**

In the “Game Options” Tab, click the Browse Button for the Executable Space. Go to the Path you extracted RTCV to and click on the executable named “RTC\_Launcher.exe”

![](../../.gitbook/assets/image%20%2833%29.png)

**4.5 Add a Custom Wine Prefix \(Optional, but Highly Reccomeneded\)**

This is if you plan on using Lutris a lot. Makes it so other wine programs don’t have a chance of conflicting with one another. It’s as simple as creating another folder.

![](../../.gitbook/assets/image%20%2854%29.png)

**5. Check the Wine Version**

In the “Runner Options” Tab, check if the Wine version if the newest availible. At the time of writing, it is Wine Staging 6.8

![](../../.gitbook/assets/image%20%2816%29.png)

![](file:///C:/Users/philt/AppData/Local/Temp/msohtmlclip1/01/clip_image012.jpg)Every other option should be setup correctly by default, you can now click on Save and close the Add Game Window.

**6. Install Dependencies via winetricks**

At the current moment the built-in Prereqs Checker does not function properly under Wine, the work around is simple.

On the main window, at the bottom there’s an Icon that looks like a Wine Glass. Click that or the arrow next to it to bring up a drop down menu.

![](../../.gitbook/assets/image%20%2853%29.png)

You then want to click on Winetricks in the menu

Then, click on “Select the Default wineprefix”

![](../../.gitbook/assets/image%20%2856%29.png)

Next, click on “Install Windows DLL or Component”

![](../../.gitbook/assets/image%20%2858%29.png)

Once you are there, look for the components – dotnet40, dotnet48, and vcrun2019

![](../../.gitbook/assets/image%20%283%29.png)

Wait for them to install, you’ll know they’re done when the “Install Windows DLL or Component” Windows appears again.  Close winetricks.

After that all you need to do is click on RTCV in Lutris and the Launcher will open, the Launcher works almost exactly like windows.

**Note:** _This guide was written on May 27th 2021. Any problems may not exist at a later date._

_**Currently, Bizhawk Vanguard, Dolphin Vanguard, and FileStub are known to work mostly as intended. Process stub only works on other applications currently running under wine. PCSX2 at the current moment does not work, as it fails to configure plugins.**_

### **Known Issues:**

**Package Downloader** has bug when you click on a category, such as PLUGIN, you can not click the BACK Button in the top left corner. You can get back by clicking Change Catalog and going back to the one you're on.

**Bizhawk Vanguard** will not detect your controller if you plug it in after launching Bizhawk. This Might not be just a wine issue.

**Dolphin Vanguard** does not always save configurations properly. In testing, Multiple controller configs had to be saved before it would remember a controller was plugged in. Volume slider in dolphin resets each time its launched. Same thing with graphics config.

_**The above issue was found using Dolphin Vanguard, but might happen on any of RTC’s Applications.**_

Infinite warnings can appear if you close dolphin before RTC closes, and then you try to close RTC while the kill-switch script is running, RTC will close, dolphin will launch again, but infinite Error messages will occur, taking away control from other windows and can quickly use up RAM. If this happens the only known solution at the moment is to Kill all Wine Process. There is a python script you can find to create a hotkey for this.

