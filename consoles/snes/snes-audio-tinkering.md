# SNES Audio Tinkering

The BSNES Core in Bizhawk can let you mess with the internals of the emulated SPC700 chip. Technically, all engine templates can give you interesting results when blasting to the **APURAM** domain alone.

There are a few particular effects that you can obtain via certain workflows. These effects, when obtained, can be sanitized and merged with other effects. Here's some examples:

**Vector engine with SPC700 lists** : Targeting the APURAM with \[SPC700]\_NOP as the Limiter and \[SPC700]\_GIGA as the Value is an easy way to get audio corruptions. These list can be found in the Package Downloader as SPC700\_Basic\_by\_BLiNX\_Person.

**Distortion Engine with Auto-Corrupt on APURAM** : The Distortion engine will always corrupt addresses using values that did previously exist in the past. This will cause things that previously happened to come back later. This will most likely desync the song tracks. Instrument changes may revert back to previous instruments.

**Pipe Engine on APURAM** : Pipe Engine on APURAM (only) with 100 Intensity and 100 Max Infinite Units is a good setup to mess up the audio rendering. Using the Glitch Harvester, you can easily Corrupt over and over to obtain particular music corruptions. The secret to this technique is that you can end up piping legal values from an address to another that cause the audio to mess up while staying stable.

