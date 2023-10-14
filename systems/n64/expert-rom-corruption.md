# N64 Expert ROM Corruption

{% hint style="warning" %}
This documentation was written with classic corruptors such as Vinesauce ROM Corruptor. That information is however still valid for corrupting the ROM domain in RTC.
{% endhint %}

## Index

* [Index](expert-rom-corruption.md#index)
  * [Super Mario 64](expert-rom-corruption.md#super-mario-64)
    * [Using Quad64](expert-rom-corruption.md#using-quad64)
    * [3D Objects](expert-rom-corruption.md#3d-objects)
    * [Macro 3D Objects](expert-rom-corruption.md#macro-3d-objects)
  * [Ocarina of Time/Majora's Mask](expert-rom-corruption.md#ocarina-of-timemajoras-mask)
  * [Other Games](expert-rom-corruption.md#other-games)
  * [References](expert-rom-corruption.md#references)
  * [Video Examples](expert-rom-corruption.md#video-examples)

For the average person, the best way to corrupt a ROM beyond what you can do with traditional N64 corruption is to do decompressed ROM corruptions with aggregates, and guess and check to find the best zones. However, if you are feeling more comfortable, there are more precise methods you can try. For the three games listed below, there are tools you can use to pinpoint the exact ranges over which you want to corrupt. These methods involve finding precise addresses of values in an N64 game, are targeting those precise ranges at a high intensity.

## Super Mario 64

To find exact ranges for Super Mario 64, you can use a map editing program like [Quad64](https://www.smwcentral.net/?p=viewthread\&t=90510) by Davideesk. Quad64 is an open source version of [Toad's Tool 64](http://qubedstudios.rustedlogic.net/ToadsTool64.htm) by Qubed Studios with cleaner UI.

![](../../assets/quad64example2.png)

The idea here is that instead of making guesses at where different values lie and then using trial and error to get good corruptions, we can look up the values we want in this tool and be more precise. Unfortunately, this tool currently only holds the values for the game's objects, but we can still get some strange results like model replacement and modified object behavior.

### Using Quad64

Upon opening the program, it will ask you to supply a ROM from which it will pull the values from. Obviously, this ROM should be the same one you intend to corrupt. I recommend using a decompressed ROM as corruption results will be more consistent when you don't have to deal with compression. I personally use a 24MB ROM, but any size decompression should be fine.

Once a ROM has been selected. you'll see a window exactly like the one above with four tabs at the top and four object types to choose from. You'll want to use the Level tab to switch between levels. If a level has more than one area to it, you can switch between them with "Select Area". The four types of objects you'll see are 3D Objects, Macro 3D Objects, Special 3D Objects, and Warps. 3D Objects and Macro 3D objects are what we plan on corrupting, and will be covered in their own sections. Special Objects are usually trees (and Bowser, for some reason) and corrupting them will only change their X and Y values so we generally don't touch them. Warps just teleport Mario to different places when they are triggered, there is little point in corrupting them.

If you open up any of these categories and click on an object, you'll get several values corresponding to that object. For our purposes, none of these values are important except for the address. The address (after the 0x) is the first hexadecimal value corresponding to the addresses associated with that object. For the last address corresponding to that object, go to the next object and subtract from it's address by one. 3D Objects will almost always be 24 bytes in size, and Macro 3D objects will almost always be 10.

### 3D Objects

3D objects tend to be highly unstable, and many values associated with 3D objects will crash the game when altered. Corrupting over the range of 3D objects will invariably cause the game to crash, and corrupting over the range with low intensity will create minimal results. Because of this, it is recommended that you try corrupting one object at a time, and combine corruptions using the Queue tool in VSRC or the merge tool in RTC. The best way to corrupt only one object is to corrupt over it's entire range with an intensity of 1 so that you hit every byte. Even when corrupting one object however, the game is likely to crash. You may need to experiment with different start bytes or increase the intensity by a little bit to get them to work. You'll get the best results by using the "Add to Byte" option and keeping the addition value small so that the object doesn't disappear or change too greatly in it's x or y value.

Another good method to make 3D Object corruptions work is to corrupt over the entire range of the object using the VSRC plugin for RTC and the glitch harvester, and then sanitize the corruption using the Random Disable 50% tool or target specific values to see what they do. This way, you can target specific behaviors while avoiding crashes. An address that tends to be useful is for objects such as enemies or bosses is the first or third address corresponds to that object's model. Look for the value in the range of about 80-110. Changing that value to 1 will replace the model of that object with that of Mario, and other values will replace it with the models of other enemies and objects depending on what pool of enemies you're pulling from. The pool of enemies depends on what cluster of levels you're currently in. Most replacement values will just make the enemy become invisible but 100, 102, 103, 104, 107, and 108 are values that often work. Doing this will make the model of on object switch with that of another, causing some bizarre behavior.

### Macro 3D Objects

Macro 3D objects are much more stable than 3D objects, but they have less variables associated with them. They are commonly objects such as groups of coins and common enemies. Because they are so much more stable, you can corrupt over the entire range of Macro 3D objects for that level with an intensity of 1 and usually not have to worry about a crash. If this doesn't work, change the intensity to 2. If this still doesn't work, keep the intensity at 2 and increase the start byte by 1. You can achieve a similar effect to this by using the Random Disable 50% tool in RTC's blast editor. To find the range over which Macro 3D Objects preside, set your start byte to the address of the first listed object and the end byte to the address of the last listed object plus 9. Again, you'll get the best results by using the "Add to Byte" option and keeping the addition value small. 1 and 2 tend to be the best values to use but you should experiment.

A lot of subtle things will change around the level with this kind of corruption, so you'll want to explore the level after you corrupt. Sometimes, Macro 3D corruption will also cause objects to use the wrong model. This is because you spawned an enemy or object which is not usually found in the level instead of the proper one. Getting too close to these objects or interacting with them will sometimes crash the game, so keep that in mind.

## Ocarina of Time/Majora's Mask

For Ocarina of Time and Majora's Mask there does not exist a level editor that reveals addresses of specific objects in the ROM. However, Ocarina of Time and Majora's Mask both have decompressed ROMs. For these ROMs, extensive ROM maps exists which give the addresses of objects and other entities in the ROM in table form. There is one for [Ocarina Of Time](https://wiki.cloudmodding.com/oot/File\_List/NTSC\_1.0), as well as documentation for Majora's Mask, which is split up into a [Actor List](https://wiki.cloudmodding.com/mm/Actor\_List) and an [Object List](https://wiki.cloudmodding.com/mm/Object\_List\_\(U\)). To follow along with either of these, you'll need to decompress your ROM. The tool of choice to decompress either Ocarina of Time or Majora's Mask is [ZDEC](http://www.mediafire.com/file/3v3v94llaqaccaj/ZDEC.rar) by VL-Tone.

Corrupting using these addresses will be similar to the process used for SM64 targeted corruption, so it's recommended that you read that section first. Like 3D objects, Actors have more pronounced and diverse corruption but are less stable. Objects are like Macro 3D objects in the same way: they're more stable but less pronounced. The File List for Ocarina of Time also gives the addresses for various other files such as textures and scenes, which are also worth experimenting with. Actors should be corrupted one at a time with similar intensity to that of 3D objects, Objects should be corrupted en masse with a corrupt every of one or two, and texture corruptions should be done in large groups but with a much larger corrupt every, similar to that of traditional decompressed corruptions. Care should be taken so that the objects or actors you corrupt are all in the area that you are actually corrupting so that you can see your results.

This section needs to be researched, and should be expanded upon in the future, but this should serve as a good basic guideline of expert corruption of Ocarina of Time and Majora's Mask.

## Other Games

Decompressed ROMs don't currently exist for N64 ROMs other than Super Mario 64, Ocarina of Time, and Majora's Mask. However, basic ROM maps exist for many games. To find them, try searching "(game title) ROM map" and seeing what you can find. For example, this is a basic [Banjo Kazooie ROM map](http://www.therwp.com/forums/showthread.php?t=15763) by Coolboyman. These games will still be more difficult to corrupt because you're going to probably find aggregates for where types of data exist, and the ROM is compressed. However, results are still possible and these ROM maps will allow for more precision when corrupting. When using ROM maps, you'll generally want to corrupt the range over which textures, models, and objects are housed. Try to pick the objects that are in the level you want to corrupt if you can. Many [RDRAM maps](https://github.com/Isotarge/ScriptHawk/tree/master/Watch) like these from Isotarge also exist for N64, but you'll need to [use RTC to corrupt those](broken-reference).

## References

The excerpts of the video below was made with [Weinerless Steve](https://www.youtube.com/user/Sevelix) and [SmellyFeetYouHave](https://www.youtube.com/user/smellyfeetyouhave)'s corruptions, and [Vinesauce](https://www.youtube.com/user/vinesauce)'s commentating, and [CaptainSouthbird](https://www.youtube.com/user/sonicepochguy)'s editing.

## Video Examples

{% embed url="https://youtu.be/cdRs8YNk1pI?t=488" %}

(8:08 to 8:29 for OoT, 8:35 to 10:34 for SM64)
