## GameBoy Advance Corruptions

### Memory Domains

* **IWRAM:** Internal \(on the same chip as the CPU\) work ram. 32kb large on a 32 bit bus. Generally holds the most critical data \(ARM code, time sensitive data, etc\)

* **EWRAM:** External \(not on the same chip as the cpu\) work ram. 256kb large on a 16 bit bus. Slower than the IWRAM. Holds anything that'd go in WRAM that isn't stored in the IWRAM. Can hold code, but since it's on a 16 bit bus it has to be ARM THUMB code

* **BIOS:** The bios, don't touch this

* **PALRAM:** Palette ram. 1KB Want to swap the colors? Have fun

* **VRAM:** Video ram. 96KB. Holds the actual data drawn to the screen.

* **OAM:** Object Attribute Memory. 1KB. Contains the actual "object" of things such as sprites \(the mode, the size, what palette to use, etc\)

* **ROM**: The ROM file

* **SRAM:** Saveram. Want to corrupt a save file? Corrupt this. otherwise it's pointless

* **Combined WRAM: **IWRAM and EXRAM combined into a single memory domain that contains both

* **System Bus:** Theoretically allows access to everything that's mapped as it facillitates the communication between pieces of hardware. In execution, not everything mapped will be visible through this domain. It's a matter of if it was properly exposed or not. Corrupt something here and it'll be reflected in the domains derived from it \(for example, the IWRAM is mapped as 0x02000000 - 0x02030000 in the system bus\)



