## Real-Time Corruptor for Bizhawk

The Real-Time Corruptor for BizHawk is a Dynamic Corruptor for emulated games. It is a mod to the Open Source BizHawk Emulator that works by modifying live data from virtual memory chips of emulated systems.



**Quick Start**

The Real Time Corruptor was designed with ease of use in mind, if you want to get right into the action simply load a ROM and click “Easy Mode” and you are away!

Obviously this is useful for those who just want instant action, but for those of you who want a more in-depth experience, this guide should help you out.

**Fundamentals**

First, let’s go over the basic fundamentals of how the corruptor functions.

Video game corruption happens when an emulated video game whose program files were altered either in the emulated game’s memory \(RAM\) or in the ROM itself. A real-time corruption is when the corruption itself occurs while the game is running or when the effects can be altered on a time basis.

**RTC **is a mod for BizHawk, which means that any emulated system that BizHawk supports \*should\* be compatible. Every system is detailed as a series of memory chips known as Memory Zones. The Real-Time corruption will be generated for the selected zones in the main window.

What is usually known as an iteration, in static corruptors, is called a Blast in the RTC. A blast consists of a series of operations that are to be applied in the code located on the emulated game’s memory banks. \(RAM, VRAM, ROM, etc.\)

**The Auto-Corrupt function **attaches the blast generation to the emulated game’s clock. Smaller blasts on a fast clock will create a constant flow of randomly generated corruption. This flow can be controlled by three parameters: The error delay, which is a divider linked to the game clock, The intensity which is a multiplier for the number of corruption units to be generated \(which depends on the selected engine\). The Blast Radius can either be SPREAD\(all corruption will be spread across the selected zones\), CHUNK \(all corruption will be sent to one single zone that is randomly selected among the selected zones\), BURST \(10 Chunks of 1/10 of the total intensity\).

  


