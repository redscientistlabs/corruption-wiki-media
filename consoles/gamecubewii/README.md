# Gamecube/Wii

### Introduction

Gamecube and Wii corruption are very similar due to the fact the Wii is essentially an upgraded Gamecube at its core.

At the moment, the best way to corrupt Gamecube/Wii is with RTC, through Dolphin-Vanguard.

{% hint style="info" %}
Recommended setup: Vector Engine   
  
Startup vector suggestions:  
**Limiter**: One, **Value**: Two  
**Limiter**: Extended, **Value**: Extended  
**Limiter**: Giga, **Value**: NOP
{% endhint %}

{% hint style="info" %}
Notable Vector Engine Combo for breaking game engine physics:  
**Limiter**: Dolphin\_PT\_FLT\_MATH, **Value**: Dolphin\_PT\_FLT\_DIV  
\*requires "Dolphin Float Passthrough" package from the Package Downloader
{% endhint %}

### Pages

{% page-ref page="dolphin-memory-domains.md" %}

{% page-ref page="gamecube-and-wii-filesystem-corruption.md" %}

{% page-ref page="gamecube-and-wii-savestate-corruption.md" %}



