# GBA Memory Domains

_Bizhawk-Vanguard exposes the following domains in RTC:_

## mGBA & VBA-Next&#x20;

* **IWRAM (Rewindable) :** Internal (on the same chip as the CPU) work ram. 32kb large on a 32 bit bus. Generally holds the most critical data (ARM code, time sensitive data, etc).
* **EWRAM (Rewindable) :** External (not on the same chip as the cpu) work ram. 256kb large on a 16 bit bus. Slower than the IWRAM. Holds anything that'd go in WRAM that isn't stored in the IWRAM. Can hold code, but since it's on a 16 bit bus it has to be ARM THUMB code.
* **BIOS** **:** The BIOS, don't touch this.
* **PALRAM :** Palette ram. 1KB Want to swap the colors? Have fun.
* **VRAM (Rewindable)** **:** Video ram. 96KB. Holds the actual data drawn to the screen.
* **OAM:** Object Attribute Memory. 1KB. Contains the actual "object" of things such as sprites (the mode, the size, what palette to use, etc).
* **ROM** : The ROM file.
* **SRAM (Rewindable, unavailable on mGBA) :** Saveram. Want to corrupt a save file? Corrupt this.
* **Combined WRAM (Rewindable)** **:** IWRAM and EXRAM combined into a single memory domain that contains both.
* **System Bus:** Theoretically allows access to everything that's mapped as it facillitates the communication between pieces of hardware. In execution, not everything mapped will be visible through this domain. It's a matter of if it was properly exposed or not. Corrupt something here and it'll be reflected in the domains derived from it.
  * `0x00000000 - 0x00003FFF`- 16 KB System ROM (executable, but not readable)
  * `0x02000000 - 0x02030000`- 256 KB EWRAM (general purpose RAM external to the CPU)
  * `0x03000000 - 0x03007FFF`- 32 KB IWRAM (general purpose RAM internal to the CPU)
  * `0x04000000 - 0x040003FF`- I/O Registers
  * `0x05000000 - 0x050003FF`- 1 KB Colour Palette RAM
  * `0x06000000 - 0x06017FFF`- 96 KB VRAM (Video RAM)
  * `0x07000000 - 0x070003FF`- 1 KB OAM RAM
  * `0x08000000 - 0x????????`- Game Pak ROM (0 to 32 MB)
  * `0x0E000000 - 0x????????`- Game Pak RAM
    * [Source](https://www.reinterpretcast.com/writing-a-game-boy-advance-game)

