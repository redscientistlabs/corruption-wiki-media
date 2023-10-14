# N64 Memory Domains

{% hint style="info" %}
The Nintendo 64's architechture supports IEEE754 Floats and is natively compatible with the Vector Engine.
{% endhint %}

_Bizhawk-Vanguard exposes the following domains in RTC:_

## Mupen64Plus core

* **RDRAM (Rewindable) :** This is the console's main RAM. It will be either 4mb or 8mb depending if the emulating N64 is using an Expansion Pack or not.
* **ROM :** This is the game's rom as perceived by the emulator.
* **MI Interface** : The registers for the CPU itself. Probably avoid this
* **PI Register :** Peripheral interface registers. Controllers and stuff
* **SI Register :** Serial Interface registers. Registers for use by anything that uses the N64's serial port
* **VI Register :** The registers for the video interface. Contains data related to drawing the current frame. Not really gonna get anything out of this besides maybe enabling some filters (such as anti-ailiasing)
* **RI Register :**
* **AI Register :** The registers for the sound chip. Doesn't actually contain the data for the music, just points to where the music is in rdram for the hardware
* **EEPROM :**
* **System Bus :**
