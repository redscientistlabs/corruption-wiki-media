# Tips, tricks and quirks

* [**Index**](tips.md)
  * [**Tips**](tips.md#tips)
    * [**Not all memory domains can be rewinded**](tips.md#not-all-memory-domains-can-be-rewinded)
    * [**Time travel to an alternate universe**](tips.md#time-travel-to-a-parallel-universe)
    * [**Playing with the settings**](tips.md#playing-with-the-settings)
    * [**Control your game from any window**](tips.md#control-your-game-from-any-window)
  * [**Tricks**](tips.md#tricks)
    * [**Rerolling**](tips.md#rerolling)
    * [**Sanitizing and merging**](tips.md#sanitizing-and-merging)
    * [**Working off existing knowledge**](tips.md#working-off-existing-knowledge)
  * [**Quirks**](tips.md#quirks)
    * [**N64 is running slow**](tips.md#n64-is-running-slow)
    * [**N64 can be quirky and unstable**](tips.md#n64-can-be-quirky-and-unstable)
    * [**Game Capture Software doesn't work properly with my RTC**](tips.md#game-capture-software-doesnt-work-properly-with-my-rtc)
    * [**Game running slow on some engines**](tips.md#game-running-slow-on-some-engines)

## Tips

### Not all memory domains can be rewinded

The default selected memory domains in RTC are supposed to be rewindable. If you select all or add more, you might end up in situations where rewind cannot erase corruption. Game Protection in Detached mode can allow for a more compatible but chunkier rewind.

### Time travel to an alternate universe

When you rewind using bizhawk, corruption also get rewinded. After you've let go of the rewind button, different corruption will be applied if Auto-Corrupt is enabled. For example, if the music dies, you can quickly rewind before it died and it should stay alive in this parallel universe.

### Playing with the settings

All the games corrupt differently. Some games may give better results with certain engines or settings.

N64 works best with Vector engine but if you are able to target specific zones using VMDs, you can get excellent corruptions with the nightmare engine.

The external ROM plugins are additional options that can allow you to get crazy results.

### Control your game from any window

Annoyed that you have to constantly click back and forth between the RTC window and the Bizhawk window in detached mode? Toggle "Accept Background Input" (Config > Customize)

## Tricks

### Rerolling

If you think you've got a masterpiece in your stockpile, try rerolling it a few times. Maybe you'll end up with something better or even completely different. Rerolling reuses the same target addresses but generates new corruption for it. You might find a case where different values in the same addresses allow you to get cooler stuff

### Sanitizing and merging

Most of the times, corruptions tend to corrupt a lot of useless addresses which can result in game crashing. Sanitizing corruptions using the Blast Editor can allow you to reduce a corruption to its minimal state. Sometimes, an interesting effect is caused by a single corruption unit. When corruptions are sanitized, they are more stable and therefore can be merged more easily. Using this method, you can craft custom corruptions with very specific effects.

### Working off existing knowledge

Some games are very well documented online. You can find documentations on ROM layouts and exploit this knowledge in order to generate VMDs and target specific areas of a ROM. The same can apply for other memory domains, if such documentation exists.

## Quirks

### N64 is running slow

By default, BizHawk doesn't enable rewind on large systems like N64 but RTC does. You can disable Large Savestates in the Rewind options.

Large Savestates require a powerful cpu and an SSD to run well. If you don't then you may very well need to disable Large Savestates for rewind.

### N64 can be quirky and unstable

When corrupting N64 games, if you're using autocorrupt or manual blast and rewind or if you "send raw to stash" and try playing back the stashed corruption, you may find that Bizhawk crashes This is a result of how the emulator works. You can prevent these crashes by changing the N64 CPU mode to "Pure Interpreter" but do note, you'll experience more crashes overall and it uses significantly more CPU.

Sometimes Bizhawk will just break and throw an error about the core accepting the rom but throwing an exception. This isn't an RTC bug, it's a Bizhawk bug. Just restart BizHawk and you should be fine.

### Game Capture Software doesn't work properly with my RTC

Having trouble capturing Bizhawk with OBS or XSplit? Try changing the display option from OpenGL to Direct3D, or vice-versa (Config > Display > Display Method).

### Game running slow on some engines

Game running slow after using the Pipe, Freeze, or Hellgenie engines? Try turning down the intensity. These engines are significantly more CPU intensive than other engines.
