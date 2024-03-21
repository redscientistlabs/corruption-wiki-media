---
description: by Brad Corrupts
---

# Corrupting the Sega Genesis

## Introduction

The Sega Genesis/Megadrive (GEN, MD) is a 16-bit fourth-generation home video game console produced, released, and marketed by Sega.

{% hint style="info" %}
Recommended setup: Nightmare engine, Hellgenie, Freeze, Pipe
{% endhint %}

## Recommended Settings

The Genesis is a system with little memory. It runs its programs directly from the ROM. The default settings in RTC are adequate for corrupting the system. If you add the System Bus or Cart ROM to the selected domains, it will unlock many more effects but make rewind unusable for uncorrupting. If you plan on using Cart ROM, you can get more results using 68000 (68K) instruction Lists.

## Expected results

Due to its age, the Genesis will very often spit out a lot of visual corruption, with some corruptions experiencing what would be colloquially called "VDP vomit," consisting of completely random pixels filling the entire screen. Games will freeze/crash when corrupted with a lot of intensity. A custom exception handler will mitigate this a bit (see below). With that said, the Bizhawk Genesis core is very stable and the Genesis very rarely causes Bizhawk itself to crash, though it is theoretically possible.

## Exception Handler

The Sega Genesis uses a 68000 CPU, which unlike earlier CPUs of the era, actually catches common CPU errors and for most games will be programmed to go into an infinite loop, thus crashing the game. To circumvent this, Brad from the YouTube channel [Brad Corrupts](https://www.youtube.com/@BradCorrupts) programmed a custom exception handler to attempt to recover when the CPU encounters an error. While it can help with game crashes, it is not foolproof. There are many other ways to crash or soft-lock the game without involving CPU exceptions. With that said, the exception handler IPS patch is provided below. Use your patching solution of choice to patch the ROM you want to corrupt.

{% file src="../../.gitbook/assets/exception handler v3.ips" %}
Exception handler IPS patch
{% endfile %}
