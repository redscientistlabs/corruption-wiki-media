# MelonDS Memory Domains

{% hint style="warning" %}
The Nintendo DS's architechture does not support IEEE754 Floats and isn't compatible with the built-in Vector Engine lists. Special lists with the NDS prefix are bundled with MelonDS-Vanguard.
{% endhint %}

MelonDS-Vanguard exposes the following domains in RTC:

* **MainRAM**: Main memory \(Dedicated WRAM for ARM9\). This contains the bulk of loaded data
* **SharedWRAM**: Shared memory between ARM9 and ARM7.
* **ARM7WRAM**: Dedicated WRAM for ARM7. Used for auxiliary tasks
* **VRAM**: Video Ram
* **CartROM**: Contains the ROM



