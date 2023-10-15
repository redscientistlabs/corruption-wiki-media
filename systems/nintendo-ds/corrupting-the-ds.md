# Corrupting the DS

### Introduction

Nintendo DS was the first handheld by Nintendo to achieve true 3D, and similarly Nintendo DS was the starting point for corruption of 3D games. It was from experimentation with corruption of this console that N64 corruption and everything after came to be.&#x20;

At the moment, the best way to corrupt Nintendo DS is with RTC and with the latest Bizhawk-Vanguard. A build of MelonDS-Vanguard is also available for compatibility with older corruptions.

{% hint style="info" %}
Recommended setup: Vector Engine with NDS Lists. \
\
Startup vector suggestions:\
**Limiter**: NDS\_One, **Value**: NDS\_Two\
**Limiter**: NDS\_Extended, **Value**: NDS\_Extended
{% endhint %}

{% hint style="info" %}
Nightmare engine also works sometimes but it is less stable
{% endhint %}

## Recommended Settings

Bizhawk doesn't come with the DS fixed-point lists preinstalled, it is recommended to get them in the Package Downloader (named VectorClassicLists\_FixedPoint.pkg)

MainRAM and SharedWRAM are where the currently loaded game stores its memory. These domains can be rewinded in Bizhawk. It is possible to corrupt DS with the ROM domain but due to the DS using compression heavily, this will rarely work. You can get more results using ARM Instruction Lists.

## Expected results

The DS is one of the few 3D consoles that can be corrupted with both the Vector Engine and the Classic Engines. Due to it being in that transition when consoles were moving to 3d, it will exhibit a lot of textures turning to clown vomit and sharp noises and pops from data entering buffers.
