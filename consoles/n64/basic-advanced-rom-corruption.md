# N64 Basic/Advanced ROM Corruption

{% hint style="warning" %}
This documentation was written with classic corruptors such as Vinesauce ROM Corruptor. That information is however still valid for corrupting the ROM domain in RTC.
{% endhint %}

## Index

* [Index](basic-advanced-rom-corruption.md#index)
  * [N64 Corruption with the Vinesauce ROM Corruptor](basic-advanced-rom-corruption.md#n64-corruption-with-the-vinesauce-rom-corruptor)
    * [Basis](basic-advanced-rom-corruption.md#basis)
    * [Setting the Values](basic-advanced-rom-corruption.md#setting-the-values)
      * [Start Byte/End Byte](basic-advanced-rom-corruption.md#start-byteend-byte)
      * [Corrupt Every](basic-advanced-rom-corruption.md#corrupt-every)
      * [Add/Shift](basic-advanced-rom-corruption.md#addshift)
      * [Replace](basic-advanced-rom-corruption.md#replace)
      * [Special Cases](basic-advanced-rom-corruption.md#special-cases)
    * [Save States](basic-advanced-rom-corruption.md#save-states)
  * [Decompressed ROM Corruptions with VSRC](basic-advanced-rom-corruption.md#decompressed-rom-corruptions-with-vsrc)
    * [Basis of Decompressed Corruptions](basic-advanced-rom-corruption.md#basis-of-decompressed-corruptions)
    * [Setting Up](basic-advanced-rom-corruption.md#setting-up)
    * [Method](basic-advanced-rom-corruption.md#method)
    * [Save States](basic-advanced-rom-corruption.md#save-states)
  * [References](basic-advanced-rom-corruption.md#references)
  * [Example Corruptions](basic-advanced-rom-corruption.md#example-corruptions)
  * [Video Examples](basic-advanced-rom-corruption.md#video-examples)

## N64 Corruption with the Vinesauce ROM Corruptor

**Guide Author: Chris Byrne (Weinerless Steve)**

This guide is currently based on [version 1.2.2](http://corruptedbytes.com/the-vinesauce-rom-corruptor/) of the Vinesauce ROM Corruptor, which is what is included with RTC and [version 2.3.2](http://www.pj64-emu.com/download/project64-latest) of Project64. Instructions may differ slightly for older versions of either. These instructions will also more or less work for VineCorrupt.

### Basis

In standard N64 corruption with the Vinesauce ROM Corruptor, our aim is to corrupt only the areas that are being loaded in real time. This allows us to specifically target things like polygon and model movement and music. Additionally, it prevents crashes by avoiding having the ROM access corrupted data in loading screens, and allows us to bypass the amount of finesse required to target specific areas of an N64 ROM by blasting a high volume of corruption over the areas.

### Setting the Values

An effective way to learn corruption is to look at an example and interpret why the values are what they are, so that will be our starting point. For a point of reference, a standard corruption of Elmo’s Letter Adventure is given below:

![](<../../assets/n64 corruption values 1.png>)

This screenshot is of VSRC, but none of these values would change with VSRC classic.

#### Start Byte/End Byte

A good way to start is to break down every value given one by one. The start byte should be above roughly 102000 no matter what N64 game you're corrupting, as anything below will cause a permanent loop error because you're corrupting crucial data in the ROM. The best way to find values that work is the set the end byte to the end of the rom and the start byte to around 102000, and if you're getting errors, bring the values of the start and end byte closer together (A good way to go about this is to use intervals of 100000 just to make things move quicker, but you might want to try increasing the start byte by just a bit at first) until you get a working corruption. If you're not seeing any sort of corruption now, move the start byte closer to the beginning or vice versa until you find the largest value that works. It is possible to corrupt a specific section of the game, like the corrupting Mario's face in the intro of Super Mario 64 by using a very small range and not needing save states. Unless you know what you’re doing, you’re likely to get nowhere attempting to be specific in what zones of the ROM you target.

#### Corrupt Every

In most cases, you'll want the "corrupt every" value between about 1 and 50. These values are so low because everything crucial to the game working is already load uncorrupted by the save state. As you probably already know, going closer to 1 will give more severe corruptions but will crash more often and vice versa. You might be tempted to try corrupting every few hundredth byte to try and get load screens to work, but you'll end up with little visible corruption and practically no results. The best place to start when you're first corrupting a ROM is around 25. There are special cases, such as Ocarina of Time, Goldeneye and Mario Party which corrupt differently than the standard ROM and will be covered later.

#### Add/Shift

Except with some special cases, the "Add to \_\_\_\_\_ byte" and "Shift Right \_\_\_\_\_ bytes" values cause pseudo-random changes in the corruptions, meaning that the parts of the ROM you’re attacking aren’t specific enough variables where you can control with any degree of accuracy what the corruption will look like based on what number you use. In a game like Ocarina of Time, this can control how far above or below the ground the character is depending on how high or low the Add/Shift number is, and in a game like Mario Party, the Add/Shift value controls what text characters replace corrupted text.

#### Replace

This option is not commonly used in N64 corruption, as replace is usually used when you want to be precise in what you’re corrupting. Because N64 corruption consists of blasting the whole ROM with little specificity, replace generally isn’t what you want.

#### Special Cases

There are a couple of special cases, and these are text corruption and what I call "object corruption". Corrupting text, which is when some text characters are replaced with other text characters or garbage text, is very similar except that you'll only see results with "corrupt every" values between 1 and about 13. Object corruption is different in that in any "corrupt every" value above 1-2, you'll get a jittery character that looks the same every time and gets repetitive quickly. Corrupting every 1-2 bytes will freeze often the character in a distorted position, creating much more interesting corruption especially when combined with the corrupted camera tilt of games like Perfect Dark and Goldeneye, and the real-time texture corruptions of games like Ocarina Of Time, which become more and more obvious the lower the "corrupt every" value is because they character is not rapidly moving and the texture corruptions are more likely to happen. You can tell whether you have a special case or not by how the game reacts when corrupted via the standard method. If the character models are stretched in weird ways but this stretching is fairly consistent, it's a normal N64 corruption. If the polygons of the character models are stretched and corrupted, it's also a normal corruption. If the character model's contortions are changing rapidly, it's object corruption, and if the text is garbled but everything else is normal (ignoring music) then you have a text corruption.

### Save States

When making the save states, you'll want to turn the corruption off and load the ROM in an unchanged state. You can make these in cutscenes or gameplay, as long as either is not pre-rendered. Avoid making them before load screens, or on menu screens. It's best to experiment to see what save states work well and what save states don't really show much corruption and go from there. To make save states, you’ll have to create them manually in your emulator of choice or use the Glitch Harvester, which is covered [elsewhere](../../corruptors/rtc/) in this wiki. Unless you've managed to find a value range where the game doesn't crash at or near startup, you'll have to load these states every single time. Keep in mind that you'll sometimes have to interact with an NPC or activate some sort of trigger before you see the effects of a corruption.

## Decompressed ROM Corruptions with VSRC

![](<../../assets/decompressed ROM corruption.png>)

### Basis of Decompressed Corruptions

Corrupting a basic ROM by blasting it with corruption and hitting only the parts that are loading in real time is not the only way to corrupt N64 games. With a decompressed ROM, you can target specific areas of the ROM, making a larger variety of corruptions possible and eliminating the need for save states, although they can still be helpful. A decompressed ROM is what it sounds like: it is an N64 ROM with the compression removed, making the ROM larger and easier to corrupt even though it still essentially runs the same.

### Setting Up

There are ROM decompression tools for 3 N64 games: Super Mario 64, Majora's Mask, and Ocarina of time. The recommended tools are: [SM64 ROM extender](https://www.smwcentral.net/?p=section\&a=details\&id=4812) by VL-Tone and [ZDEC](http://www.mediafire.com/file/3v3v94llaqaccaj/ZDEC.rar), which is for Ocarina of Time and Majora’s Mask and also created by VL-Tone. There is another Super Mario 64 decompression tool with more options called [sm64extend](http://origami64.net/showthread.php?tid=97) which is not recommended because it creates larger extended ROMs then the ones used to make the example corruptions. You can circumvent this by specifying the size that you want your extended ROM to be, but unless you want to mess around with the more technical options of sm64extend this is an unnecessary extra step. If you intend to follow with the N64 corruption examples given, you need the right version of Super Mario 64, which can be found denoted as Super Mario 64 (U) \[!]. If you're not sure you have the right ROM, try a corruption and see if it works as intended. The SM64 ROM should be about 24 MB if this process was done correctly. Example corruptions for each of these games and a text file with a rough mapping of the SM64 ranges can be found below.

To run these with Project64, you need to run the decompressed ROM you want to corrupt, and go into Options>Settings>Config (ROM name) and change the memory size to 8MB. Otherwise, you'll just get a black screen because the emulator doesn't have enough memory to map in. However, if you are using RTC and Bizhawk this step is unnecessary.

### Method

Decompression of ROMs spaces out the ROM in question, making it much easier to access a specific part of a ROM that you are trying to reach as you can deal with greater ranges and don’t have to work around compression which can make targeting specific areas far less effective. The best results can be found by looking to find the parts of the ROM that control textures, models, or anything else desired, and isolate this part to get the result you want with as few crashes as possible. A good way to go about this to look for specific parts in blocks of 100,000 at a time (such as corrupting from 900K to 1M) and widening or shortening the range to get better results. If the part you’re trying to corrupt is toward the end of the ROM, it’s not a bad idea to just corrupt to the end of the ROM as this can cause some corruptions to behave differently but is unlikely to cause crashes. This part of the ROM does not create much corruption on it’s own, but can modify the effects of existing corruptions in earlier parts of the ROM. You'll want to have the "corrupt every" higher with these, with the 75-120 range being optimal in most cases. Depending on what part I'm trying to corrupt, I've gone as low as 45 or as high as 160. It all depends on what aspect of the ROM you are trying to corrupt, and the best way to figure out the value you want is trial and error like everything else with N64 corruption.

Along with the decompressed corruptions I've included a small text file with the ROMs and examples that show some of my findings for ranges in SM64 decompressed. This may help give an idea of how ROMs work and help with corrupting other decompressed ROMs as well.

### Save States

Unlike the model corruptions, which we've been doing earlier in the guide, most of these are activated by loading screens. If you're trying to load a texture scrambling corruption, for instance, you'd be best off using a save state that takes you to the screen before the place you want to see corrupted. You're not really aiming for every single load screen to work, but you want enough where you're able to see the results of your corruption without it being too unstable. Music corruptions can be an exception to this rule, but this is a rule you usually need to follow.

While save states aren’t required, it’s still helpful to make them anyway. Whether a load screen will crash the game or not can be inconsistent within a single corruption. Therefore, you want to make multiple save states before and after load screens to make sure you don’t miss any good results. For example, if I was corrupting Super Mario 64 I would put one at the menu screen in case the game crashed starting up, one outside the castle, inside any major section of the castle, and a couple in the levels themselves. I would also have a save with no stars so I could see what the intro looked like corrupted, and a save with stars so I could see as many individual levels as I wanted corrupted. If you want quick access to all the levels in a game, you can always use Gameshark codes to unlock everything and then make your save states from there.

## References

This wiki article is adapted from the [N64 Corruption Guide 1.1.5](https://web.archive.org/web/20160519231533/http://vinesauce.com:80/vinetalk/viewtopic.php?f=34\&t=98). Credit goes to Nephkin for finding the range for the SM64 corruptions of Mario’s face and [SmellyFeetYouHave](https://www.youtube.com/user/smellyfeetyouhave) for the idea of the decompressed ROM corruptions. The videos below were made with [Weinerless Steve](https://www.youtube.com/user/Sevelix)'s corruptions, and [Vinesauce](https://www.youtube.com/user/vinesauce)'s commentating and editing.

## Example Corruptions

(These corruptions were found by Weinerless Steve and many of these corruptions are the same ones found in Vinesauce’s videos as Steve submitted these corruptions to him. If you plan on using these corruptions without modification in your own videos, please credit Weinerless Steve. If you choose to find your own using these as a starting point, no credit is necessary)

[Decompressed ROM Corruptions](http://www.dropbox.com/sh/0x8n01kqwmmlel6/HyptNZP3Bc)

[Elmo's Letter Adventure](https://www.dropbox.com/sh/idnk0nzx0hdktf0/DTt5Vezfzn)

[Perfect Dark](https://www.dropbox.com/sh/8210223azlyie0b/WYb6WNMWYf)

[Super Mario 64 Face Corruptions](https://www.dropbox.com/sh/lfaxy26nvkk1sk9/Vji8jfRe5Z)

[Super Mario 64 Movement Corruptions](https://www.dropbox.com/sh/lagac9vj7xw4lhu/spiDPotgye)

[Donkey Kong 64](https://www.dropbox.com/sh/o0n337gqt5mjqs9/J6MtMENySV)

[Legend of Zelda: Ocarina Of Time](https://www.dropbox.com/sh/jl147aectlhvvoo/UCSfeVXf-\_)

## Video Examples

{% embed url="https://www.youtube.com/watch?v=ZIMQ9NIB-sA" %}

One of the more popular corruption videos and a good example of object corruption.

{% embed url="https://www.youtube.com/watch?v=OvNDcVRlyYk" %}

The first iteration of decompressed ROM corruptions and one of the most well known corruption videos to date.
