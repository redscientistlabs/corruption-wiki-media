# Introduction

The Real-Time Corruptor for BizHawk is a Dynamic Corruptor for various uses. Far more capable than your usual rom corruptor, the RTC works by modifying live data from the virtualized memory chips of emulated systems allowing data corruption in real-time. As of version 5, RTC can connect to a variety of emulators and tools (called Stubs) for corrupting all sorts of uses.

### Quick Start

The Real-Time Corruptor was designed with ease of use in mind, if you want to get right into the action simply start an emulator from the launcher, load a ROM and click “Easy Start” then "Start with Recommended Settings" and you are away! (_Instant results not always guaranteed. Some emulators require bios or firmware files which you must acquire legally)_

#### Video tutorial on using RTCV for corrupting with Dolphin

{% embed url="https://www.youtube.com/watch?v=SD20GFosdts" %}
Credit: Gizmo The Dragon - Youtube&#x20;
{% endembed %}



## Download: [https://redscientist.com/RTC](https://redscientist.com/rtc)

**All programs from the RTC suite of tools are Open Source and available at: **[**https://github.com/redscientistlabs**](https://github.com/redscientistlabs)****

First, let’s go over the basic fundamentals of how this corruptor functions.

![Modded emulators, stubs and extra stuff can be downloaded from the RTC Launcher](<../../.gitbook/assets/image (34).png>)

Video game corruption happens when an emulated video game's program files are altered, either in the emulated game’s memory (RAM) or in the ROM itself. A real-time corruption is when the corruption itself occurs while the game is running or when the effects can be altered on the spot.

**RTC **is a collection of modified emulators and stub tools that integrate our corruption software via a solution we called Vanguard. This means that any emulator or program that is modded with Vanguard _should_ be compatible. Every system's memory areas are detailed as a series of zones known as Memory Domains. The corruption will be generated for the selected domains in the main window.&#x20;

__

_**Take note that this guide was written with emulated game corruption in mind. All details of how internals work will be described for the use of a Vanguard modded emulator. Usage with stubs & wgh may differ.**_

_****_

What is usually known as an iteration in static corruptors, is called a Blast in the RTC. A blast consists of a series of operations that are to be applied in the data located on the emulated game’s memory banks. (RAM, VRAM, ROM, etc.)

**The Auto-Corrupt function **attaches the blast generation to the emulated game’s clock. Smaller blasts on a fast clock will create a constant flow of randomly generated corruption. This flow can be controlled by three parameters: The **Error Delay,** which is a divider linked to the game clock, The **Intensity **which is a multiplier for the number of corruption units to be generated (which depends on the selected engine). The **Blast Radius** determines how the corruption is spread on the selected domains.

### Frequently asked questions

The Real-Time Corruptor generates corrupted data independently from the memory it perceives and stores it, making it possible to easily replay, share, modify and analyze corruption results. Whenever RTC fires corruption, it creates what we call a Blast Layer and then Applies it onto the game's memory, which is the action of what we call a Blast.

**RTC doesn't start on my computer**

\-> Have you installed the prereqs for BizHawk? This is essential for BizHawk to run properly. You can grab those from there too: [http://tasvideos.org/BizHawk.html](http://tasvideos.org/BizHawk.html)

\-> Make sure your computer is decent. It must be strong enough to run the games and RTC does add a slight increase on the system requirements.

** Why does RTC wants to be allowed in the Windows Firewall?**



RTC uses networking for a bunch of stuff. As it's split between two processes, they need a way to communicate. To do this, they use TCP and UDP. This will prompt the Windows Firewall and if it is not allowed, RTC will not function properly. If you blocked it by accident, you can reverse the rule in the advanced windows firewall panel.

** BizHawk : Why are certain emulator cores running slow or RTC running slow in general ?**

BizHawk is one hell of an emulator. It features a ton of emulator cores and tools to create Tool-Assisted Speedruns. In order for these speedruns to be accurate to the real-life systems that they emulate, some of those do extra operations and disable optimizations that might cause faster but inaccurate emulation.

Some emulator cores are faster than others. QuickNes is generally faster than NesHawk for example.

\-> Make sure you have the latest .Net Framework installed on your computer

**BizHawk : Why doesn't RTC work with LibRetro cores in BizHawk?**

All normal cores within BizHawk should work fine although a libretro core loaded into Bizhawk won't work. If you run into issues, join the RTC Discord and we can provide support.

**Can I add a new emulator to RTC?**

Absolutely! We provide all of our source code so that you can mod Vanguard into any program and examples for already modded emulators. If you are up for the challenge, you should probably come talk with us on the Discord and we'll give you some help if needed.

**Why is the emulator i'm using going slow when Auto-Corrupt is on?**

Auto-Corrupt does add an extra load to the emulator as it must execute some extra code on every frame, on top of already having to execute Active Units. Certain types of Units are harder to process than others.

**Visit the **[**Tips, tricks and quirks**](https://corrupt.wiki/corruptors/rtc-real-time-corruptor/4.html)** part of the guide for more details**
