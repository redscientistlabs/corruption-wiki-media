## Real-Time Corruptor for Bizhawk

The Real-Time Corruptor for BizHawk is a Dynamic Corruptor for emulated games. It is a mod to the Open Source BizHawk Emulator that works by modifying live data from virtual memory chips of emulated systems.

**Quick Start**

The Real Time Corruptor was designed with ease of use in mind, if you want to get right into the action simply load a ROM and click “Easy Start” and you are away! \(_Instant results not always guaranteed\)_

**Fundamentals of RTC**

First, let’s go over the basic fundamentals of how this corruptor functions.

Video game corruption happens when an emulated video game whose program files were altered either in the emulated game’s memory \(RAM\) or in the ROM itself. A real-time corruption is when the corruption itself occurs while the game is running or when the effects can be altered on a time basis.

**RTC **is a mod for BizHawk, which means that any emulated system that BizHawk supports _should_ be compatible. Every system is detailed as a series of memory chips known as Memory Domains. The corruption will be generated for the selected domains in the main window. Certain engines/plugins may ignore the selected domains as part of their design.

What is usually known as an iteration in static corruptors, is called a Blast in the RTC. A blast consists of a series of operations that are to be applied in the data located on the emulated game’s memory banks. \(RAM, VRAM, ROM, etc.\)

**The Auto-Corrupt function **attaches the blast generation to the emulated game’s clock. Smaller blasts on a fast clock will create a constant flow of randomly generated corruption. This flow can be controlled by three parameters: The **Error Delay,** which is a divider linked to the game clock, The **Intensity **which is a multiplier for the number of corruption units to be generated \(which depends on the selected engine\). The **Blast Radius** determines how is the corruption is spread on the selected domains.

