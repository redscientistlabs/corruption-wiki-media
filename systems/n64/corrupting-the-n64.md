# Corrupting the N64

## Introduction

&#x20;The Nintendo 64 is a home video game console developed and marketed by Nintendo. In its own generation, it was more powerful than the PS1 but lacked the Optical disc storage space for games. Unlike the PS1, the Nintendo 64 was compliant with IEEE754 floats.

{% hint style="info" %}
Recommended setup: Vector engine on RAM domain

Startup vector suggestions:\
**Limiter**: One, **Value**: Two\
**Limiter**: Extended, **Value**: Extended
{% endhint %}

## Recommended Settings

The N64 is a complete departure from what you'd see in more classic systems like NES, SNES, Gameboy, Genesis. The entire system relies on a pool of either 4mb or 8mb of Ram which is accessed by the whole machine. This is called the RDRAM in the memory domains and it is the best domain to target. The ROM can also be corrupted with the memory domains but it is most of the time compressed data unless you're using a decompressed rom. You can get more results using MIPS Instruction Lists.

## Expected results

The N64 being an early 3D console doesn't make extensive use of shaders and physics. Due to that, the corruptions will most likely affect models. Disapearing and stretching tris is to be expected.

## Improving emulator stability

Bizhawk's latest builds do not have an N64 core with a dynamic recompiler. This makes corruptions less stable than its earlier versions. The RTC Launcher has a compatiblity build called "Bizhawk Legacy" that exclusively improves stability for N64.

It's worth noting that corruptions found with that version can sometimes be moved to a newer version of Bizhawk after they've been sanitized.

##
