# Bizhawk Memory Domains

## BSNES

* WRAM \(Rewindable\) : The console's main memory
* CARTROM : Contains the ROM
* VRAM \(Rewindable\) : Video RAM, contains Tile Data and the Tile Map
* OAM \(Rewindable\) : Object Attribute Memory. "OAM contains all the properties of your sprites, such as the X coordinate, Y coordinate, tile \#, vertical flip, etc \(All will be listed shortly\). OAM can only hold properties for up to 128 sprites at a time. Also, OAM addresses are a word in size." [_ref_](https://wiki.superfamicom.org/snes-sprites)\_\_
* CGRAM : Color Graphics Ram. This is where the color palette data is kept
* APURAM : Audio Processing Unit Ram. This is where audio data is kept
* System Bus :

## Snes9x

* WRAM \(Rewindable\) : The console's main memory
* VRAM \(Rewindable\) : Video RAM, contains Tile Data and the Tile Map
* CARTROM : Contains the ROM

## Documentation references

[https://wiki.superfamicom.org/snes-sprites](https://wiki.superfamicom.org/snes-sprites)  
[https://wiki.superfamicom.org/working-with-vram-initializing-tiles-and-tile-maps](https://wiki.superfamicom.org/working-with-vram-initializing-tiles-and-tile-maps)

