# Emulators

## Recommended Emulators for Corruptions

This is a list of emulators that are recommended for use when corrupting games or recording corruptions, this list takes into consideration the ease of use and the compatibility with the "Launch emulator" option in some corruption tools rather than the accuracy or the game-compatibility of the emulator.

#### Note that this list is for manual ROM corruptions or to be used the Vinesauce ROM Corruptor \(VSRC\) or Cheat Engine. The Real Time Corruptor is built along-side Bizhawk which is a suite of various emulator cores, so it is not necessary to use any external emulators with it.

## NES

## ![](../.gitbook/assets/nes.png)

### Nestopia

It's one of the most popular and compatible emulators around, traditionally used in lots of corruption videos because of it's ease of use and how it seamlessly launches corrupted ROMs via the VSRC.

## SNES

![](../.gitbook/assets/snes.png)

### Snes9x

SNES9x is the oldest and most popular SNES emulator for the PC because of it's ease of use. It launches corrupted games via the VSRC just fine.

### ZSNES

ZNES has been in development since 2001 and has an interesting non-standard UI and runs ROMs via the VSRC just fine. **NOTE: ZSNES has a serious vulnerability allowing for executing arbitrary code \(potentially malware\) if allowed to load a tampered ROM. Using ZSNES with SNES ROMs gotten from unknown sources is thus not recommended.**

## N64

![](../.gitbook/assets/n64.png)

### Project64

PJ64 is an easy to use N64 emulator and is fairly tolerant to corrupted ROMs, careful when you download from the site as it has ads in the installer.

### 1964

1964 isn't as popular as other N64 emulators but it is reminiscent of PJ64 as it has a similar GUI and is able to launch ROMs via corruptors seamlessly.

## PS1

![](../.gitbook/assets/ps1.png)

### XEBRA

XEBRA is relatively unknown in the corruption community but it's easy to use, corruptions work fine, and it has video upscaling so you make record high quality videos with it. To download go to the bottom of the page and click on the first image.

### psxfin

psxfin is outdated and old but just works. You can run most games and launch them through the VSRC just fine, the GUI is easy to follow and controller setup is simple.

## NDS

### ![](../.gitbook/assets/ds.png)

### DeSmuME

DeSmuME is the go-to DS emulation software for the PC, it's accurate, somewhat maintained and has upscaling on 3D models for higher quality videos, it launches ROMs through any corruptor just fine.

## PC

**\(x86\)**

### Qemu

While the VSRC cannot "corrupt an OS" you can corrupt a game in a virtual environment using Cheat Engine or any other memory hacking tools. You can use Qemu to launch any OS and run your emulators, games and corruptors within it to achieve corruptions in a virtual environment. Qemu will also virtualize other OS architectures like MIPS or i686 based OSes. The only downside is that it is not so easy to set up.

### VirtualBox

VirtualBox is basically the same as Qemu except it has an easy to follow GUI that runs all common OSes in an x86 environment. The only downside of VirtualBox is that it doesn't virtualize anything other than x86 and x86\_x64.

### VMWare

Similar to Virtualbox, VMWare is another virtualization solution with an easy to use GUI. It runs all common OSes. VMWare has the best DirectX support of the the options provided here.

