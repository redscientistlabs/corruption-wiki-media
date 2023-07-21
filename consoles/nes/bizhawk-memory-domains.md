# NES Memory Domains

## QuickNes

* **RAM** (Rewindable) : Contains the console's main RAM
* **WRAM** (Rewindable) : Work RAM
* **CHR** (Rewindable) : Sprite memory
* **CIRAM (nametables)** (Rewindable) : Area of the PPU where the backgrounds are stored
* **PRG ROM** : Main Program ROM (From .nes file)
* **CHR VROM**: Main Character data (From .nes file)
* **PALRAM**: Palette RAM. Changes colors
* **OAM** (Rewindable) : Object attribute memory (sprite flags and locations)
* **System Bus**: Main memory bus where everything is mapped on

## NesHawk

* **RAM** (Rewindable) : Contains the console's main RAM
* **System Bus** : Main memory bus where everything is mapped on
* **PPU Bus** (Rewindable) : Sprite memory
* **CIRAM (nametables)** : Area of the PPU where the backgrounds are stored
* **OAM** (Rewindable) : Object attribute memory (sprite flags and locations)
* **Battery RAM** : Memory space for saving on cartridge
* **PRG ROM** : Main Program ROM (From .nes file)
* **CHR VROM** : Main Character data (From .nes file)
* **WRAM** : Work RAM
