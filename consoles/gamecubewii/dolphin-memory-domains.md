# Dolphin Memory Domains

{% hint style="info" %}
The Nintendo Gamecube and Wii's architechture supports IEEE754 Floats and are natively compatible with the Vector Engine.
{% endhint %}

Dolphin-Vanguard exposes the following domains in RTC:

* **SRAM** \(24MB\): Main system memory. Game code is usually stored here.
* **ARAM** \(16MB\): Mainly used to store data related to audio, can also be used by games to store additional data that isn't related to Audio
* **EXRAM** \(64MB\): Additional memory exclusive to the Wii.

