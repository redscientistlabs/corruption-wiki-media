# Corrupting the 3DS

## Corrupting the 3DS

### About the System

The 3DS is an ARM-based Nintendo handheld console that succeeded the Nintendo DS. It shares many attributes, such as a foldable design, while also adding new features for developers to use. Most importantly, Nintendo added a floating-point processor for enhanced 3D graphics. As such, its corruption process is very similar to other 3D systems, such as the GameCube/Wii and PS2.

As of 5.2.0, the best way to corrupt the 3DS is with Bizhawk via the RTC Launcher. For prior versions, you must use the Citra emulator, which is slower and less stable.



### Recommended Settings

Use VMDs extensively

Vector Engine with Default RTC Lists

Limiter: Extended -> Value: Extended

Limiter: One -> Value: Two



Vector Engine with Lists from the Package Downloader: VFP-Specific Lists

Limiter: VFP\_Load and store -> Value: ARM\_NOP

Limiter: VFP\_Math -> Value: ARM\_NOP



The custom VFP lists from the Package Downloader are the best for corrupting the 3DS. They provide consistent results without many crashes. You can also use other ARM lists, but they are less stable and will usually crash.

In addition to the Vector Engine, creating VMDs (#link=Virtual Memory Domains) is crucial for getting results on the system. The target area for each domain is large, and the data is very concentrated. The FCRam domain in the range 7000000-8000000 houses most of the code, so it’s a good idea to create a VMD within that range to start.

