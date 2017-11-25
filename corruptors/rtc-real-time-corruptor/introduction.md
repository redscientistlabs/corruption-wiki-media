# Real-Time Corruptor for BizHawk

###### Author: [Phil Girard](http://redscientist.com/)

###### Source: [https://github.com/ircluzar/RTC3/](https://github.com/ircluzar/RTC3/)

###### Download: [http://redscientist.com/\#/rtc](http://redscientist.com/#/rtc)

The Real-Time Corruptor for BizHawk is a Dynamic Corruptor for emulated games. It's a mod to the Open Source BizHawk Emulator that works by modifying live data from the virtualized memory chips of emulated systems.

{% youtube %}https://www.youtube.com/watch?v=CqSsD91Nzw4{% endyoutube %}

* [**Introduction**](#index "Literally this")
  * [**Quick Start**](#quick-start)
  * [**Fundamentals of RTC**](#fundamentals-of-rtc)
  * [**Frequently asked questions**](#frequently-asked-questions)
  

#### Quick Start

The Real Time Corruptor was designed with ease of use in mind, if you want to get right into the action simply load a ROM and click “Easy Start” then "Start with Recommended Settings" and you are away! \(_Instant results not always guaranteed\)_

#### Fundamentals of RTC

First, let’s go over the basic fundamentals of how this corruptor functions.

Video game corruption happens when an emulated video game whose program files were altered either in the emulated game’s memory \(RAM\) or in the ROM itself. A real-time corruption is when the corruption itself occurs while the game is running or when the effects can be altered on a time basis.

**RTC **is a mod for BizHawk, which means that any emulated system that BizHawk supports _should_ be compatible. Every system is detailed as a series of memory chips known as Memory Domains. The corruption will be generated for the selected domains in the main window. Certain engines/plugins may ignore the selected domains as part of their design.

What is usually known as an iteration in static corruptors, is called a Blast in the RTC. A blast consists of a series of operations that are to be applied in the data located on the emulated game’s memory banks. \(RAM, VRAM, ROM, etc.\)

**The Auto-Corrupt function **attaches the blast generation to the emulated game’s clock. Smaller blasts on a fast clock will create a constant flow of randomly generated corruption. This flow can be controlled by three parameters: The **Error Delay,** which is a divider linked to the game clock, The **Intensity **which is a multiplier for the number of corruption units to be generated \(which depends on the selected engine\). The **Blast Radius** determines how is the corruption is spread on the selected domains.

#### Frequently asked questions

**What is the difference between Attached Mode and Detached Mode?**

Detached mode is the default mode in RTC 3. It detaches RTC and Bizhawk in two processes and lets them communicate through a homemade system called NetCore. This allows RTC to stay alive if BizHawk crashes and allows for game states to be kept saved outside of BizHawk when using "Game Protection".

RTC Multiplayer is exclusive to Attached Mode since it uses the NetCore to connect two RTCs together. In Attached Mode, you can use the Classic AutoKillswitch by opening it from the Launcher or via the Settings Menu.

Detached Mode has its own embedded AutoKillswitch.

**RTC doesn't start on my computer**

-&gt; Have you tried stock Bizhawk? Do note, that as of Bizhawk 2.x, Bizhawk is 64bit only and supports operating systems Windows 7 and upwards. RTC 3.10 is based on Bizhawk version 2.2.1 which can be obtained here: [http://github.com/TASVideos/BizHawk/releases/download/2.2.1/BizHawk-2.2.1.zip](http://github.com/TASVideos/BizHawk/releases/download/2.2.1/BizHawk-2.2.1.zip)

Alternatively, the "Start BizHawk without RTC" option will load BizHawk without the Mod.

-&gt; Have you installed the prereqs? This is essential for BizHawk to run properly. you can grab those from there too: [http://tasvideos.org/BizHawk.html](http://tasvideos.org/BizHawk.html)

-&gt; Make sure your computer is decent. If it's too old then maybe the rendering options of BizHawk may not work. We've seen that problem happen with old Core2Duo chipsets for computers using Internal Graphics.

** Why does RTC wants to be allowed in the Windows Firewall?**

RTC uses networking for a bunch of stuff. Here's more details about those:

-&gt; Loopback UDP: Used for the Auto-KillSwitch and External ROM Plugins

-&gt; Loopback TCP: Used for Detached Mode \(StandaloneRTC communicating with Modded Bizhawk\)

-&gt; TCP: Used for RTC Multiplayer

The features mentioned above WILL NOT WORK if RTC isn't allowed in the firewall.

** Why are certain RTC Cores running slow or RTC running slow in general **

BizHawk is one hell of an emulator. It features a ton of emulator cors and tools to create Tool-Assisted Speedruns. In order for these speedruns to be accurate to the real-life systems they emulate, some of those do extra operations and disable optimizations that might cause faster but inaccurate emulation.

Some emulator cores are faster than others. QuickNes is generally faster than NesHawk for example.

Unfortunately, if the whole thing is still too slow, your only solution might be to upgrade your computer. For comparison, RTC works just fine on a mobile 2nd-Gen Core i3.

**A certain Emulator core doesn't work with RTC**

This problem usually happens with snes9x. It's not working. The problem is on BizHawk side. One day they'll finish porting it I guess.

**Can RTC work with another emulator than BizHawk?**

The mod could probably be ported, but that would require a ton of modifications, and that's only possible if the other emulator is open source. At this point in time, there's more chances that the Windows Glitch Harvester gets ported for other emulators than RTC, due to a more generic approach in WGH's design.

**Visit the [Tips, tricks and quirks](https://corrupt.wiki/corruptors/rtc-real-time-corruptor/4.html) part of the guide for more details**




