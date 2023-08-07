# Frequently Asked Questions



### **RTC doesn't start on my computer**

\-> Have you run the Prereqs Checker in the launcher?

\-> Make sure you have the latest .Net Framework installed on your computer

\-> Make sure your computer is decent. It must be strong enough to run the games and RTC does add a slight increase on the system requirements.

\-> Certain Emulators may have difficulties with certain hardware. Try another emulator if it doesn't work

### &#x20;**Why is Bizhawk slower than other emulators ?**

\-> BizHawk is one hell of an emulator. It features a ton of emulator cores and tools to create Tool-Assisted Speedruns. In order for these speedruns to be accurate to the real-life systems that they emulate, some of those do extra operations and disable optimizations that might cause faster but inaccurate emulation.

Some emulator cores are faster than others. QuickNes is generally faster than NesHawk for example.

\-> You can play around with (or disable) the Rewind settings to make emulation less heavy on your system.



### **Why doesn't RTC work with LibRetro cores in BizHawk?**

All normal cores within BizHawk should work fine although a Libretro core loaded into Bizhawk won't work. The Libretro support in BizHawk is not good enough yet, we'll support it when it reaches stability comaparable to RetroArch



### **Can I add a new emulator to RTC?**

Absolutely! We provide all of our source code so that you can mod Vanguard into any program and examples for already modded emulators. If you are up for the challenge, you should probably come talk with us on the Discord and we'll give you some help if needed.



### **Why is the emulator i'm using going slow when Auto-Corrupt is on?**

Auto-Corrupt does add an extra load to the emulator as it must execute some extra code on every frame, on top of already having to execute Active Units. Certain types of Units are harder to process than others.



### How do I get to the emulator's folder?

Using the RTC Launcher, select the RTC Version and then right click on the emulator of your choice. Select the option "Open Folder" to open the Emulator's folder.



### How do I add Firmware files to BizHawk?

BizHawk expects its firmware files to be in the Firmware folder. You can check which Firmwares are properly installed from the window in the top menu, at Config -> Firmwares.

\-> We CANNOT give you the files you need. They are copyrighted and you have to find them on your own.



### **How do I add Firmware files to MelonDS?**

MelonDS expects its firmware files to be installed in the Emulator folder (where the melonDS executable is). Open the folder by right clicking the emulator card in the launcher and selecting "Open Folder" then drop the files in the Windows Explorer window.

Pay extra attention to the filename of the Firmware files you give to MelonDS as it REQUIRES that they are written in all lowercase, exactly as shown in the error window when starting it.

If the error message still appears after putting the files in the folder, you did something wrong. Check all the filenames and ensure that they are IDENTICAL to the ones in the error message.

\-> We CANNOT give you the files you need. They are copyrighted and you have to find them on your own.





**Visit the** [**Tips, tricks and quirks**](../../corruptors/rtc/tips.md) **part of the guide for more details**
