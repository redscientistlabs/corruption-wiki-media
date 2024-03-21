---
description: by Brad Corrupts
---

# Genesis Memory Domains

_Bizhawk-Vanguard exposes the following domains in RTC:_

## Genplus-gx

* **68K RAM (Rewindable):** Genesis main RAM region run by the 68K. 64KB large on a 16-bit bus. Main memory containing variables, data structures, etc. Rarely, if ever, contains actual code.
* **Z80 RAM (Rewindable):** SPU work ram run by the Z80. 8KB large on an 8-bit bus. Sound engine and data are stored here. Note that some games use the 68K for their sound engine (Sonic 1 being a notable example).
* **MD CART:** The ROM file.
* **BOOT ROM:** The BIOS for the Sega/Mega CD. Don't touch this, unless you're doing BIOS corruptions.
* **CRAM (Rewindable):** Palette ram. 128 bytes. (Not recommended. Some games refresh CRAM every frame. Also looks to be broken in this build.)
* **VSRAM (Rewindable):** Vertical Scroll RAM. 128 bytes. (Not recommended. Only affects vertical scroll position in the game.)
* **VRAM (Rewindable):** Video ram. 96KB. Holds the actual data drawn to the screen.
* **System Bus:** Theoretically allows access to everything that's mapped as it facilitates the communication between pieces of hardware. In execution, not everything mapped will be visible through this domain. It's a matter of whether it was properly exposed or not. Corrupt something here and it'll be reflected in the domains derived from it.
  * `0x000000 - 0x3FFFFF`- 4MB Cartridge ROM (MD Cart)
  * `0x400000 - 0x7FFFFF`- Reserved (used by the Sega CD and 32x)
  * `0x800000 - 0x9FFFFF`- Reserved (used by the 32x?)
  * `0xA00000 - 0xA0FFFF`- Z80 addressing space (8K RAM mapped to x0000-0x1FFF)
  * `0xA10000 - 0xA10001`- Version register (read-only word-long)
  * `0xA10002 - 0xA1001F`- I/O Registers
  * `0xA11000`- Memory mode register
  * `0xA11100 - 0xA11101`- Z80 bus request
  * `0xA11200 - 0xA11201`- Z80 reset
  * `0xA14000 - 0xA14003`- TMSS register
  * `0xC00000 - 0xC00009`- VDP registers
  * `0xFF0000 - 0xFFFFFF`- 64KB 68K RAM **Sega CD Changes**
  * `0x000000 0x01FFFF`- BIOS ROM
  * `0x020000 0x03FFFF`- "Program RAM" Bank Access
  * `0x200000 0x23FFFF`- "WORD RAM"
  * `0xA12000 0xA120XX`- "Gate Array"
  * `0xFFFD00 0xFFFDFF`- Interrupt/Exception vectors
    * [Source](https://en.wikibooks.org/wiki/Genesis\_Programming/68K\_Memory\_map/)
