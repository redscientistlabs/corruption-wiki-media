---
description: by Mismagius
---

# Advanced corruptions

## Corrupting the PSX (Advanced)

### Introduction

The Sony PlayStation (PS1/PSX) is a 32-bit system released in 1994 in Japan and 1995 in North America and Europe. With a focus on 3D polygon graphics rather than sprite-based rendering, the system achieved massive success through its lifespan, being the birthplace of many of the staple franchises in the gaming landscape. The PlayStation was the main focus point when transitioning from cartridges to compact discs, as it could hold a much larger amount of data, allowing streamed content such as audio and video sequences to appear much more frequently.

| <p>Recommended setup: Vector Engine<br></p><p>Limiter: _[MIPS]_AllBranches, Value: _[MIPS]_AllBranches</p><p>Limiter: _[MIPS]_AllBranches, Value: _MIPS_NOP</p><p>Limiter: _[AnySystem]_AnyFixedPoint, Value: _MIPS_NOP</p><p></p><p>Recommended Intensity: 50-200</p> |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Recommended Settings

The PSX is much more finicky than systems such as the NES/SNES due to its complexity and usage of MIPS architecture. As it does not use floating point values, most of the default RTC lists will not work for the system. A good starting point is to download the “MipsInstructions” and “MipsLoadAndStore” lists from the RTC Package Downloader, as well as the “VectorClassicLists” and “MIPS Immediate” packages. The “Wildcards” and “RandomBitFlipLists” packages can be useful as well, albeit rarely, and only once you know what you are doing.

\
With its 2MB of RAM, 32-bit MIPS architecture and BIOS exception/opcode handler, you will struggle to get anything other than a crash with most engines (namely Nightmare, Hellgenie, Pipe, Freeze, and Distortion engine). 90% of the time, you will be using the Vector Engine. The Cluster Engine can be very useful as well, but it requires some understanding of the engine itself as well as the memory areas you are messing with. For starters, it is better to stick with Vector Engine until you get your footing. With proper usage of VMDs, even the other engines can be useful, so if you already have that knowledge from other consoles, it will be useful.

\
We will talk about the PSX MainRAM in more detail later, but in short, for most games it is rarely ever worth messing with anything other than the MainRAM. For starters, you can keep it as your only selected domain. The GPURAM will specifically target textures and sprites. The SPURAM will only mess with the audio, but keep in mind that we’re messing with streamed audio here, which doesn’t allow for much other than popping sound and maybe repeating audio lines. BiosROM, unless you’re messing with the BIOS itself and not a game, won’t do anything other than crash the system. DCache won’t usually do anything worthwhile and the System Bus is simply all of these together.

\
As for Vector Engine settings, you will notice “Limiter” and “Value” lists. You can read more about it in the Vector Engine section of the wiki, but when talking about Vector Engine settings, always assume the format \[Limiter list] -> \[Value list]. Regarding Intensity, you will usually end up with very low values, often under 100, but you can always adjust based on how often you are getting no results or crashes. It’s also important to check the Stash History and right-click the latest iteration to check how many units are being affected by your current settings. Also don’t forget to lock your precision to 32-bit and alignment to 0!

\
For a starting point, pretty much any of the MIPS lists will work as a limiter using MIPS\_NOP as a Value list (or Zero, which is the same thing).

\
Branch lists (AllBranches, BEQ, BLTZ, BNE, J, JAL) will mostly work with NOP. You can attempt playing around with using BEQ -> BNE and vice-versa, or even AllBranches -> AllBranches, but this will be much more unstable and prone to crashing, although useful at times..

\
Memory Access lists (SB, SH, SW, LB, LBU, LH, LHU, LW) will pretty much only work with NOP due to the way the MIPS architecture is set up. There’s always a possibility you can get a unique result using a list into itself, but you’ll have to be patient (and lucky).

\
Fixed Point register lists (Extended, One, Two, Whole) are heavily dependent on the game you are corrupting. Some games tend to use these values more often especially when corrupting data (models, images, pointers) rather than code. These lists are less prone to crashing when playing around between themselves, but Extended and Whole as limiter lists -> One, Two, NOP as value lists should be the more consistent setting for these.

### Expected Results

As previously mentioned, the PSX is a very, very crashy system. However, this is due to the way it allocates its memory. When corrupting the MainRAM, you aren’t just focusing on 3D models, images, sounds or data, you’re taking on everything at the same time and often switching around data that is completely incompatible. As the PSX has a pretty hefty exception handler, the game will 99% of the time just completely freeze once something wrong is detected. You can easily check whether the system is dead by enabling the “View -> Display FrameCounter” setting on BizHawk and noticing when the numbers go red and stop counting up.



With the recommended settings above, you will hopefully have a bit more luck playing around with the system. However, there are many other ways you can avoid smashing your head into a wall repeatedly for 30 minutes until you get a missing polygon. Most of them will require some basic knowledge of RTC and/or the system’s architecture, but it is definitely worth it!



Most of the effects you will notice when corrupting the PSX with the MIPS lists will affect the game’s logic, differently than the NES/SNES, where it is more common to get clown vomit and audio corruptions. Since games will often store audio, video and models using raw data, you can mostly affect the way they are rendered on screen, but hardly ever change their properties with lists alone.



As for intensity, it can be hard to gauge exactly how much is a good amount. Usually you can do some guesswork. If it instantly crashes, it’s too high. If it does nothing, it’s too low. Try to find an in-between until results start appearing. It doesn’t mean it won’t crash or always produce an effect, but it should be the optimal intensity amount.

| ![](https://lh7-us.googleusercontent.com/BXZ\_\_6LAoFlFyByRg8mEx3M5FwE-FWV5F4osQv1NllppnwOPEx2UdYxL5sM5PzPBLlGbUBN3ugX7ViJPbeE8O1ZJsAdVTacESiAd1TlNetIzONmdNyOvjdNOfjKWjeB5oewfym55vsFAybq7DHg-5Ag)  | <p>An example of texture corruption effects.</p><p><br></p>         |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| ![](https://lh7-us.googleusercontent.com/YDIoucR0748zF-RVjhAwF98a\_-6w1dC\_MyM7zBdHbQ6Y7ONYKet3JNYX9mIl3amhDiAF0hB8\_BQvLws0jnzfT6-bStB9kNXncYXu89pFls4HSD7O8x0TBmHSLmMhxia7AZVAfy9I9MuR6XtCLzdX9wM) | <p>An example of model/rendering corruption effects.</p><p><br></p> |
| ![](https://lh7-us.googleusercontent.com/FusGZtFy\_y05GtyrCosGBBUMM4rWFXeC0zNp1vvUx8U62D09mfxbXsuuI\_RClbR9mEEER6iiW\_KAyzeP-hWdpRl3ZmK3rpsGYEmB3lovwq0ALqc8atrD4B7nxpDV0UguMneAct99nEfU8DQKkGS5Iuc) | An example of code corruption effects.                              |

## PSX: Working with the MainRAM

When we delve into the PlayStation’s MainRAM, we are working with 2MB of data, which means 2,097,152 bytes where the current state of the game is loaded, including all current code, animations, models, sounds and everything else the game feels like it needs to have on hand. This may seem overwhelming at first, but don’t worry! When corrupting memory addresses, we will have to get used to hexadecimal notation as it is used internally, so the MainRAM constitutes everything between the addresses 0x80000000 and 0x80200000. For the sake of corruptions, it’s easier to simplify it to 0 until 200000.



Remember that we are dealing with a CD-based system and CDs can hold up to about 700MB of data! This means that we probably won’t be loading/storing anything more than 10% of the CD’s contents into RAM, so there is no easy way we can effectively “perma-mod” a game’s data using corruptions, as corruptions will just take the current game state and replace things until the game loads something else into the system RAM and move on. The most we can do in this case is target the base code to make it so the game will always be loading/storing data in a certain way.



Back into the addresses, instructions are stored in 32-bit chunks, usually aligned evenly. That means that, unless you are targeting an instruction individually with 8bit corruptions, the RTC will always default to hitting 4-byte precision addresses ending in 0, 4, 8 and C. For example, this is how a Vector Engine blast -> NOP will look like. Notice the addresses and the amount of zeros we are replacing the data with:



<figure><img src="https://lh7-us.googleusercontent.com/d-MBPHhSiU_NrosWOkTteoT1jnSGw1qGAwfc9jVVq3UksdLLtcB-oq7UKUvpnQ2DZVvbfqOyt0OB4ELw9-LHYh4biN_Dz8dbq7StHN52rMB6y4OyAxNGg1CqonR9jtBuj1l9x_AA4cHXnKpa9cWHdCc" alt=""><figcaption></figcaption></figure>

This means that, between the addresses xxx00 and xxx10, there are 4 possible instructions we can target: xxx0, xxx4, xxx8 and xxxC.



Considering the MainRAM, the area between addresses 0 and 10000 is reserved for the PSX BIOS. Attempting to corrupt anything in there will almost always result in either nothing or a crash. Therefore, if you have any knowledge about VMDs at this point, you already know where we are heading into!\


<figure><img src="https://lh7-us.googleusercontent.com/aFRcsDE5sjVy6DK7hXz3b5kDbDdPnPJ_XYQhC5dnf7nIYuRvctB7kyV-rxdJR5YA3pGuhgimb6jjqIQ5D8T31mRUl5O8clWOFwOb2tok2PO_eOdALuZZFcyd03eCy67KN0oWHP7s90vL2Oe3GIXat6Y" alt=""><figcaption></figcaption></figure>

This is an example of a VMD you could make to remove that part of the RAM when corrupting. As we will see in a moment, it won’t be the most accurate way to target things, but it’s a good start, already taking out 3% of the memory that would be essentially useless to corrupt.



After the BIOS segment, games are free to handle memory as the programmers see fit. This means that there is no standard way to divide things from now on, so be aware that this is completely game specific! What works in a game will most definitely not work on another game, especially regarding specific address ranges. The best we can do is define a couple common things that happen in PSX games.



First of all, starting on address 10000, unless specified by the developers, the game will often contain the main executable. This is the first file in the disc that will be read, and often contains basic functions and instructions for the game to start running. There is no set amount of data for this main executable, as there are games that hold the entire thing in it. You can try searching the internet to see if anyone has made a memory map of the game you want to corrupt, or try and open the contents of the game’s ISO and identify the main executable and its size (it will often be called something like PSX.EXE or SLUS\_12.345).



After that, PSX games will often use “overlays”, which are chunks of code or data that are loaded separately from the main program. As they are often not listed in the CD-ROM directory and each game has its own completely separate layout, there is no real way to identify these without disassembling the code itself. So what’s the point of everything written up until this point? Well, we can establish a fairly decent way of guessing what we are messing with, based on the results we see on each corruption and looking at the address they are located in.

1. BIOS (0-10000);
2. Game main executable (starting on 10000, often basic functions, such as VSync, video rendering, and loading everything else);
3. Game specific functions will usually be loaded after this, which will define how characters, animations, audio, behaviour, etc. are defined on screen.
4. After everything else, the game may contain the raw files of images, models, animation data, and MIDI sequences. These are generally stored in common PSX file formats such as .TIM, .ANM, .VAB, etc. As such, targeting specifically instructions here will often not hit anything!

\
Again, this does not cover every possible PSX game! There is a massive amount of games that use all kinds of different methods of storing into RAM. As the PSX has a rather limited amount of RAM for everything it is trying to load, the usage of memory can be very dynamic and some addresses will not always reflect the same thing depending on game state. Not to mention things such as the VRAM buffer, stack and other parts that will be constantly shifting data around every single frame.



A common, helpful practice for people messing with PSX corruptions is to create VMDs for sequential chunks of memory. This helps on mapping out what parts of memory you can mess with to achieve certain results. For example, having 20 VMDs, with 16k of RAM each. VMD1\[0…10000], VMD2\[10000…20000], VMD3\[20000…30000], and so on. Soon, you’ll end up getting used to which VMDs target what parts of the code, and locate yourself whenever you want to look for an effect.

## PSX Architecture

Did you know that there are many other instructions you can target besides the ones in the default lists? The MIPS I architecture has a multitude of other instructions and pseudo-instructions that are often used for PSX games. For the scope of this writeup, we’ll try and keep things mostly simple and focused on corruptions, so expect some heavy simplification, but at the same time you are expected to understand basic computer architecture concepts such as binary and assembly code. This is not at all necessary if you just want to get some basic corruptions, but it will be extremely helpful if you want to have as much control as possible over the state of the game.

\
Arithmetic Logic Unit: ADD, ADDI, ADDIU, ADDU, AND, ANDI, LUI, NOR, OR, ORI, SLT, SLTI, SLTIU, SLTU, SUB, SUBU, XOR, XORI

\
Shifter: SLL, SLLV, SRA, SRAV, SRL, SRLV

Multiply: DIV, DIVU, MFHI, MFLO, MTHI, MTLO, MULT, MULTU

Branch: BEQ, BGEZ, BGEZAL, BGTZ, BLEZ, BLTZ, BLTZAL, BNE, BREAK, J, JAL, JALR, JR, MFC0, MTC0, SYSCALL

Memory Access: LB, LBU, LH, LHU, LW, SB, SH, SW



What these all have in common is that their last 6 bits (as the PSX uses little-endian) store the opcode of each function. After that, we can separate them into three different groups:



R-Type instructions (Shifter, Multiply, JR, JALR, ADD, ADDU, SUB, SUBU, AND, OR, XOR, NOR, SLT, SLTU): These instructions are identified by an opcode of 0, and are differentiated by their funct values. Except for SLL/SRL/SRA, these operations only use registers.



J-Type instructions (J, JAL): These instructions are identified and differentiated by their opcode numbers (2 and 3). The rest of the bit fields are used for the target address.



I-Type instructions (everything else): These instructions are identified and differentiated by their opcode numbers (any number greater than 3). All of these instructions feature a 16-bit immediate.

\
Alright, so what does any of this mean for corrupting? Well, first of all, it means that rarely ever you’d want to use two different types of instructions on Vector Engine blasts. As the bit fields have different purposes, you’ll just end up losing a lot of time by not knowing you weren’t supposed to use something such as SLL -> J.



This also helps in identifying what you are currently blasting. By disabling your blast units and opening the Hex Editor in the desired addresses, you can check what you ended up hitting and how to take maximum advantage of blasting that address. Say you got an interesting effect by blasting NOP on a SLL instruction. Who’s to say you can’t keep it as a SLL and only change the registers you are targeting, or the amount of shifting? The possibilities are endless.



In the Resources section, you will find more information on how these instructions work and lists for each instruction. Keep in mind some of these will not bring you any results for corruptions, but others may surprise you with different effects than what you’d get on the default lists.

## Resources



[Plasma - most MIPS I(TM) opcodes :: OpenCores](https://opencores.org/projects/plasma/opcodes) - List of most common MIPS I opcodes. Useful for when you want to identify what is the instruction in a specific address, and how to alter it without crashing the game.

[Exploring Tokimeki Memorial: Main Index](https://tetracorp.github.io/tokimeki-memorial/) - Very interesting project focused on reverse-engineering the PSX game Tokimeki Memorial, gives a rundown on how to analyze a game’s code and find points of interest in the RAM and executables.

[psx-spx](https://psx-spx.consoledev.net/) - Extremely detailed documentation on everything about the PSX’s internals, built from years of guesswork and development.

[MIPS Converter](https://www.eg.bucknell.edu/\~csci320/mips\_web/) - Hex/Instruction converter, useful to quickly get what’s happening in a specific address, as well as converting your own assembly code to hex to put it back into the game.

[MIPS Reference Sheet](https://inst.eecs.berkeley.edu/\~cs61c/resources/MIPS\_help.html) - More in-depth explanation for each instruction in the MIPS set.

[MIPS Multiply Lists](https://cdn.discordapp.com/attachments/901853587557204041/1176556924809003068/MIPS\_MLT.zip?ex=656f4d06\&is=655cd806\&hm=2ef652fccc9974f9510ee988d72ed5c3ba8ec9c3b477c38027b9ff0c133298ab&) - Lists that cover the Multiply instructions in the MIPS set.

[MIPS ALU Lists](https://cdn.discordapp.com/attachments/901853587557204041/1176557940283547779/MIPS\_ALU.zip?ex=656f4df8\&is=655cd8f8\&hm=246b3c145d9d487b6174668b61b79d76e4b3f48f25fb183978f4327b7f301c94&) - Lists that cover the Arithmetic Logic Unit instructions in the MIPS set.

[MIPS Shift Lists](https://cdn.discordapp.com/attachments/901853587557204041/1176558242432823376/MIPS\_SHIFT.zip?ex=656f4e40\&is=655cd940\&hm=44a53a97006b30b2dd553f84b2a688f44d18a80382a542d07528ce629f6942ee&) - Lists that cover the Shifter instructions in the MIPS set.

[MIPS Branch Lists](https://cdn.discordapp.com/attachments/901853587557204041/1176558651448754206/MIPS\_BRANCH.zip?ex=656f4ea1\&is=655cd9a1\&hm=b308ba82ace2830df871be38c92ede8873e38a9debad34edfb47e3e9ed1631a3&) - Lists that cover the Branch instructions in the MIPS set.

[MIPS Memory Access Lists](https://cdn.discordapp.com/attachments/901853587557204041/1176558896643592232/MIPS\_LS.zip?ex=656f4edc\&is=655cd9dc\&hm=f5bc5ffe066a550ecb9d2270798f275943deb438380546dd1e4394833079dbb0&) - Lists that cover the Memory Access instructions in the MIPS set.

[BradCorrupts' Patched PSX BIOS](https://cdn.discordapp.com/attachments/479047343589687308/1160363792744599562/scph1001\_-\_exception\_bypass\_-\_1.0.ips?ex=656bc2fe\&is=65594dfe\&hm=edb183d457e3e5f7a3b532096ac7e475c7bdb9018ea123cfa6019745db755b7a&) - WIP. Patches your PSX BIOS to try and bypass the exception handler, avoiding game crashes. [Requires specific setup.](https://cdn.discordapp.com/attachments/901853587557204041/1176559588049436782/image.png?ex=656f4f81\&is=655cda81\&hm=2eecd003c3e6da350c15aa055298ecf17b3492b9dd88446f6d7bf81bde7b051a&)

\
