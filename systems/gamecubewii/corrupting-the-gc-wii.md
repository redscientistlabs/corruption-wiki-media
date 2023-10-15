# Corrupting the GC/Wii

### Introduction

Gamecube and Wii corruption are very similar due to the fact the Wii is essentially an upgraded Gamecube at its core.

At the moment, the best way to corrupt Gamecube/Wii is with RTC, through Dolphin-Vanguard.

{% hint style="info" %}
Recommended setup: Vector Engine \
\
Startup vector suggestions:\
**Limiter**: One, **Value**: Two\
**Limiter**: Extended, **Value**: Extended\
**Limiter**: Giga, **Value**: NOP
{% endhint %}

{% hint style="info" %}
Notable Vector Engine Combo for breaking game engine physics:\
**Limiter**: Dolphin\_PT\_FLT\_MATH, **Value**: Dolphin\_PT\_FLT\_DIV\
\*requires "Dolphin Float Passthrough" package from the Package Downloader
{% endhint %}

## Recommended Settings

Systems emulated with Dolphin are arguably the most stable of the emulated 3d consoles. Because of that, you could possibly corrupt a lot with the Classic Vector Lists and turn the game into pulp before it crashes. The Auto-selected domains are the one to use. Avoid old engines such as Nightmare, Hellgenie, Freeze, etc. You can get more results using Dolphin Instruction Lists.

## Expected results

These system exhibit the golden standard in terms of corruption results. The stability of the emulator makes it much simpler to harvest effects. When using instruction lists, expect the classic Wii crash noise.
