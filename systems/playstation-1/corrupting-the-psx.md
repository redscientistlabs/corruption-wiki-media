---
description: by Mismagius
---

# Corrupting the PSX

## Corrupting the PSX

### Introduction

Corrupting the PSX is quite complex when compared to NES and SNES, and can be more difficult than floating point based systems such as the GC/Wii, but it’s still quite feasible for beginners.

| <p>Recommended setup: Vector Engine</p><p></p><p>Limiter: _[MIPS]_AllBranches, Value: _[MIPS]_AllBranches</p><p>Limiter: _[MIPS]_AllBranches, Value: _MIPS_NOP</p><p>Limiter: _[AnySystem]_AnyFixedPoint, Value: _MIPS_NOP</p><p><br></p><p>Recommended Intensity: 50-200</p> |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Recommended Settings

For most games it is rarely ever worth messing with anything other than the MainRAM. The GPURAM will specifically target textures and sprites. The SPURAM will only mess with the audio, but doesn’t do much other than popping sound and maybe stuttering. BiosROM won’t do anything other than crash the system when corrupting a game. DCache won’t usually do anything worthwhile and the System Bus is simply all of these together.

\
For Vector Engine settings, any of the MIPS lists into MIPS\_NOP (same as Zero) will work most optimally. AllBranches also works into AllBranches as well as it does with NOP. You can also take the \_\[AnySystem]\_AnyFixedPoint (or Any32) lists and pair them with a NOP, but these will usually need very low intensity. In general we’re talking anywhere from 10 intensity to 200.

### Expected Results

Most of the effects you will notice when corrupting the PSX with the MIPS lists will affect the game’s logic, differently than the NES/SNES, where it is more common to get clown vomit and audio corruptions. Since games will often store audio, video and models using raw data, you can mostly affect the way they are rendered on screen, but hardly ever change their properties with lists alone.\


| ![](https://lh7-us.googleusercontent.com/Bj9v5wxtUZ2roHPfXFm1X3gb5z1rR7JgwfzMBasy\_UiAKbKcCcCPpXjyi68KSvJUAD7hCA6LemlWqawf4zaOXU3Ej4\_nKiWicA0SuOgp4-\_l5uDfBZUYH77YHlOpKM7CgRREhUcah7-SabeTxd9CHLg)     | <p>An example of texture corruption effects.</p><p><br></p>         |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| ![](https://lh7-us.googleusercontent.com/\_xyV5EMbzsl4RBDe7U\_wTtpoDLbeo3rRZUez\_KYGaxSEndcfTTjKOqm6\_yM9DlH3SayfQ6kJ0qFtjSZUqB67ykkBK1oHktn3MLzWXNzF-8xl0\_I\_8JjzL7mR4Gm\_HHGj-ggSWvaMo8WQv8vP57agC5s) | <p>An example of model/rendering corruption effects.</p><p><br></p> |
| ![](https://lh7-us.googleusercontent.com/GzbZX9Jgax4WHrqmkxmH4WisUSbiTlIyyu1fY7IljIjY\_tjbTAkNBdaf869Pn5IdnQ1zSD8Rosuca2b7\_suTctPyoKRyhmIR5wA4cgm1cj9ZkbJy7WqMiKDhlda-EMlhcGV1Csmlofbn-cLgIM1np6k)      | An example of code corruption effects.                              |

\
