# Emulation-centric features

Some components run in the RTC process and some of them run in the Emulator process. Some features of RTC are designed to either enhance emulation experience, stability or bind corruption features to the emulator.

### Auto-KillSwitch

![](<../../.gitbook/assets/image (2) (1).png>)

In order to give the user the smoothest experience, RTC will constantly monitor the state of the connected [Vanguard-Modded](concepts-and-vocabulary.md#vanguard) emulator and attempt to kill it if it falls into a non-responsive state.

_If the heartbeat between RTC and the emulator stops for a long period, the progress bar will indicate the remaining time before the KillSwitch fires automatically._

While many emulators can have their games crash gracefully, they can sometimes freeze or enter an infinite loop if the game crash couldn't be handled properly. This can be detected and RTC will then proceed to kill and restart said emulator.

_When the Auto-KillSwitch is triggered, the user will hear a sound of broken plates, confirming that the emulator has been terminated. Said sound can be changed, replaced or muted in the Settings and tools._

### Game Protection

![](<../../.gitbook/assets/Game Protection.png>)

The Game Protection optional feature has two benefits for the user:

* Keeps regular backups of the game's state in case of a crash
* Allows for a pseudo-rewind feature that works across all Real-Time Implementations

If the emulator crashes while Game Protection is enabled and there's at least one saved item, the game will reload the most recent state when it comes back up.

The Back/Now buttons allow for the user to browse the constantly updating list of savestates in order to rewind back, similarly to BizHawk's rewind feature but in bigger chunks of time.

_It should be worth noting that Game Protection increase the power requirements for a smooth experience. An SSD is required to prevent "hitching", although this is not always the case with every emulator/core. Mileage may vary._

### Rewindable Domains

In BizHawk, all emulator cores come with Rewind capabilities. At the time of writing this guide, no other emulator than BizHawk supports native Rewind (among the ones modded with [Vanguard](concepts-and-vocabulary.md#vanguard)).

By default, RTC will select [Memory Domains](concepts-and-vocabulary.md#memory-domain) that are **Rewind-safe**, meaning that the data edited in these domains can be rewinded out of. Reverting back the corruption that occurs in domains that aren't rewind-safe requires the selection of "Reboot Core" in the emulation menu of BizHawk or reloading a [Glitch Harvester Savestate](glitch-harvester.md#savestate-manager) or [StashKey](concepts-and-vocabulary.md#stashkey).

It should be worth noting that RTC's Game Protection feature can act as a pseudo-rewind as it allows the user to jump back in the past using savestates. This feature should be available to any emulator with a Real-Time [vanguard implementation](concepts-and-vocabulary.md#vanguard).
