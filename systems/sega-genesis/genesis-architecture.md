---
description: by Brad Corrupts
---

# Genesis Architecture

[Genesis Architecture, a Practical Analysis](https://www.copetti.org/writings/consoles/mega-drive-genesis/)&#x20;

[Genesis memory map](https://segaretro.org/Sega\_Mega\_Drive/Memory\_map)&#x20;

[Genesis ROM Header, including vector tables](http://www.hacking-cult.org/?r/18/21)

## CPU

The Sega Genesis uses a [Motorola 68000](https://en.wikipedia.org/wiki/Motorola\_68000) as its main processor.

[M68000 Microprocessor User's Manual](https://www.nxp.com/docs/en/data-sheet/M68000UM.pdf)&#x20;

[Motorola 68000 CPU Opcode Table](http://goldencrystal.free.fr/M68kOpcodes-v2.3.pdf) (Good reference for creating instruction lists)&#x20;

[68000 ASM-to-Hex Code Reference](https://info.sonicretro.org/SCHG:68000\_ASM-to-Hex\_Code\_Reference) (Good reference for hacking machine code by hand)

## APU

The Sega Genesis uses a [Zilog Z80](https://en.wikipedia.org/wiki/Motorola\_68000) as a coprocessor, mainly for driving the [Yamaha YM2612](https://en.wikipedia.org/wiki/Yamaha\_YM2612) and [Texas Instruments SN76489](https://en.wikipedia.org/wiki/Texas\_Instruments\_SN76489).

[Genesis Z80 memory map (among other technical information)](https://md.railgun.works/index.php?title=Zilog\_Z80#Memory\_Map)

[Z80 Microprocessor User's Manual](https://www.zilog.com/docs/z80/UM0080.pdf)&#x20;

[Z80 Opcode Tables](https://clrhome.org/table/) (Good reference for creating instruction lists)

[Yamaha YM2612 technical documentation](https://www.smspower.org/maxim/Documents/YM2612)&#x20;

[Texas Instruments SN76489 technical documentation](https://retrocdn.net/images/e/e0/SN76489\_Application\_Manual.pdf)

## GPU

The Sega Genesis uses a proprietary Yamaha YM7101 Visual Display Processor (VDP).

[Sega Genesis Software Manual](https://segaretro.org/images/a/a2/Genesis\_Software\_Manual.pdf) (See section II)
