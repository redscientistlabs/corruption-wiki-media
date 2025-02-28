---
description: Plugin and Guide made by PurelyAndy
---

# Java Corruptor Plugin

{% hint style="info" %}
NOTE: If you have no other custom layouts installed, the Java Corruptor layout will load automatically when clicking "Load Custom Layout".
{% endhint %}

{% embed url="https://www.youtube.com/watch?v=lq2zc9v22hI" %}
Video Tutorial
{% endembed %}

## Introduction

The Java corruptor is a plugin made to easily corrupt games written in Java. It was written with similarity to the usual RTC experience in mind, so your prior experience with RTC will be applicable when using it. This overview will cover the behavior of the different engines, important facts about Java to keep in mind, and notable differences between the Java corruptor and RTC.

## Prerequisite Java information

The JVM (Java Virtual Machine) is a stack machine, which means that each instruction ran modifies a figurative stack of values. An instruction might switch items around on the top of the stack, remove an item from the stack, add one, add/remove multiple, or any combination of these. It's important that when you corrupt the bytecode, it will result in the stack having the same value on it as it did originally. If you run an instruction that removes a value from the top of the stack, but there are no items left, Java will detect this when the affected class is loaded, and the program will crash. If you try to return from a method with more than one value on the stack (or any at all in the case of a void), the program will crash. If you replace an instruction that takes a different type of value from the stack than the original, the program will crash. You can find a list of each instruction, its operands, and its stack behavior [here](https://en.wikipedia.org/wiki/List_of_Java_bytecode_instructions).

## Normal usage

The Java corruptor plugin makes use of FileStub for loading files as input, and its interface is loaded from the Custom Layout item in RTC's sidebar. The plugin comes with custom replacement controls that replace the main window's usual tools. If a Vanguard implementation other than FileStub is loaded, a file without a .jar extension is loaded, or multiple files are loaded, the plugin will automatically hide itself and its custom layout. There are FileStub templates available for Minecraft and Project Zomboid from the dropdown box at the top of the window, under "Target Type". More information about those games can be found in their respective wiki articles.

## Java blast units

A Java blast unit includes the fully-qualified name/descriptor of the method to corrupt, the index of the instruction to corrupt, a number of instructions to replace starting from the index, and a list of instructions to place there instead. If the `Replaces` value is set to 0, the instructions will be inserted _after_ the index without removing anything.

## General parameters

**Intensity**\
The chance that an instruction will be corrupted, if it matches the criteria for the selected engine.

**Launch a software after corrupting**\
Lets you select/create a "launch script" that runs programs after corrupting the game. For example, you might run a batch script to replace the old JAR file with the corrupted one, then run the game with a Java command.

**Use last seed**\
Lets you corrupt the game with the same random values as last time. This was added for debugging purposes, but can be handy to more easily re-roll a corruption with different settings.

### Settings

**When corrupting, compute:**\
All stack frames: Tells ASM to recompute all the stack frames in the corrupted method. This is necessary to run any corruptions that contain labels without running your game with the `-noverify` JVM argument. This only applies to the custom engine, and only if you write an engine that uses branches and labels.\
Max stack size: Tells ASM to compute only the maximum size of the stack. This is the default as it is significantly faster and doesn't cause issues for most use cases.

**Compress corrupted JAR**\
JAR files are basically renamed zip files, so this option compresses the JAR in case you're low on storage. It is disabled by default as it can be quite slow.

**Threads**\
Runs the corruptor across multiple threads to improve speed. On the machines I've tested, 4-5 is the fastest, with lower or higher values running more slowly. Cranking this up to the max will not speed it up.

**Limit domain to classes/methods**\
Allows you to specify which classes/methods the corruptions may affect. If no methods are selected, every method in the selected class(es) is allowed by default.

## Re-rolling corruptions

The Java corruptor plugin has a method of re-rolling blast units different to the standard RTC re-roll feature. Each unit has the engine used to create it saved within, as well as the engine's settings. You can edit a unit's settings by right-clicking it in the blast editor and clicking "Modify Re-roll Settings". Besides that, units are re-rolled the same way as you normally would in RTC.

## The disassembler

The disassembler can be a useful tool when editing blast units or writing a custom engine. It allows you to read the Java bytecode instructions within a method, and see their indexes. It can be opened by clicking the "Open Disassembler" button in the general parameters or by right-clicking a unit's method and clicking "Disassemble this unit's method".

## Common errors and their causes

Sometimes you'll corrupt your game and run into a 'Cloud Debug' box. Sometimes the errors within these have known fixes.

**System.OverflowException**: If RTC freezes for an extended period after applying a corruption, and this error shows up after, something is wrong with the logic in your units. You may be accidentally sharing labels between units.

**System.IO.InvalidDataException: End of Central Directory record could not be found**: Your .jar file is likely open, or in-use by software such as 7-zip or WinRAR.

**Number of entries expected in End Of Central Directory does not correspond to number of entries in Central Directory**: See above

**System.ArrayTypeMismatchException: Source array type cannot be assigned to destination array type**: It's uncertain what exactly causes this issue, but some Fabric Minecraft mods cause this to occur, including Distant Horizons.

## Engines

Each engine has an effective default configuration except for Basic engine and Nuker engine.

### Basic Engine

This is arguably the easiest-to-use engine. It just replaces any of the selected Find instructions with any of the selected Replace with instructions. It only includes instructions that do not have any operands. When you select an instruction, only other compatible instructions will be shown. The most effective instructions are the ones that begin with F or D.

**Replaces:** 1 instruction\
**Creates:** 1 instruction

### Arithmetic Engine

This engine adds an extra math operation to be performed on the result of an various instructions.

**Instructions**\
Which sorts of instructions should be corrupted.

**Limiter operations**\
If "math operations" is selected under instructions, which operations are allowed to be corrupted.

**Value operations**\
The operations to perform on whatever is being corrupted.

**'Int', 'Float', 'Long', and 'Double' check boxes**\
These let you choose which types should be corrupted. Floats and doubles are generally the best to corrupt. Checking 'int' will also corrupt math done on shorts and bytes.

**Minimum and Maximum**\
The engine chooses a random value between these numbers to perform the new operation with. For ints and longs, the value is always rounded towards zero (1.5 rounds down to 1, but -1.5 rounds up to -1.)

**Randomize value at runtime**\
This decides whether the extra operation should be performed with a constant value, or with a different one between the minimum and maximum each time the corrupted code is run.

**Skip array accesses**\
If variable loads or stores are selected in the instructions list, skip instructions for the contents of arrays.

**Replaces:** 1 instruction\
**Creates:** The original instruction, and with 'randomize value at runtime' off, 2 more. With 'randomize value at runtime' on, 9 more.

### Function Engine

This engine replaces calls to any of the selected limiter functions with any of the selected value instructions. The "POP,random()" option discards the value that would be passed to the original function, and replaces the function with Math.random() which returns a value between 0 and 1.

**Replaces:** 1 instruction\
**Creates:** 1 instruction, or 2 for "POP,random()"

### Custom Engine

This engine allows you to create your own engine with regular expressions (regex). You can right-click the Corruption Engine title bar to pop the window out and resize it for more space, and you can resize the two sections by clicking between the text boxes and dragging. Before corrupting, use the "Check For Errors" button to ensure that the engine won't generate any invalid instructions. It will simulate your engine on every instruction in the currently loaded JAR, then report back with which lines produced errors and why. If your engine produces invalid instructions in the test, but you decide to corrupt with it anyway, expect a cloud debug box to show up when the plugin fails to parse a broken instruction string.

**Find**\
A list of instructions to corrupt. Opcodes must be in ALL CAPS. All text in a line after `//` is ignored. Multi-line comments are also supported with `/*` at the beginning and `*/` at the end. Regexes should be put in \<angle brackets>. You may not use named groups within your find group, because they require usage of the `<` and `>` characters. Regex subroutines are also not allowed because .NET does not support pattern recursion. Prior to corrupting, all `$`s at the ends of lines are removed, the first line of the find section has `^` prepended, and the last has `\r?$` appended.

**Replace**\
A list of instructions to replace the original ones with. Opcodes must be in ALL CAPS, and comments are supported. You can reference capture groups in the find section like `<$1>`. Multiple references combined like `<$1$2$3>` will not work. To generate a random single-precision floating-point number, use the syntax `<randomF 0.5,2.5>`. You can do the same with doubles, longs, and ints with `randomD`, `randomL`, and `randomI`. Your engine can also employ some basic logic. Say you want to add a random number between 1 and 10 to floating-point addition instructions every time the code runs. If you have a find section like `<(F|D)ADD>`, you could add the code `<if $1 == F>D2F<else>NOP</if>` to convert the result of `Math.random()D` to a float with a `D2F` instruction only if the original instruction was `FADD`. If you need logic at runtime, you'll have to use labels and branch instructions. You can't use a static name for each label, though, because if a function gets corrupted with multiple blast units, all of their instructions will point to the first label\*. Instead, use `<label YourLabelName>` to name your labels. For example:

```
INVOKESTATIC java/lang/Math.random()D
LDC 0.5D
DCMPG
IFLE <label LessThanHalf>
FSUB //if random() was >= 0.5, FSUB
GOTO <label MoreThanHalf>
<label LessThanHalf>: //if random() was < 0.5, FADD
FADD
<label MoreThanHalf>:
```

This will ensure that a unique set of labels is used for every blast unit.

_\*Due to a quirk in the code, the generated blast units actually will have properly separated labels and will load correctly, but the initial blast will be broken. If multiple blast layers are applied, all units from the same methods will share labels._

**Replaces:** Depends\
**Creates:** Depends

### String Engine

This engine edits text within the code. It is quite crash-prone, and better results can be gained from Nuker engine's string tab.

**Characters**\
The text the engine will use when corrupting. Each mode uses them differently.

**Percentage**\
The (approximate) percentage of the string to corrupt.

**Nightmare mode**\
Replaces characters from the original string with random characters from the 'characters' box. Example: "This is a string of text" > "Thxs iska splang ojptext"

**Swap mode**\
Swaps characters with each other around. Example: "This is a string of text" > "hTis ia srst ing xf teot"

**Cluster mode**\
Like swap mode, but only with adjacent characters. Example: "This is a string of text" > "hTis i sa stirng of txet"

**One-per-line mode**\
Replaces the whole string with one of the lines of text from the 'characters' box. Does not respect the percentage value. Example: "This is a string of text" > "This is the text on line 3!"

**Only Strings with Spaces**\
Makes the engine only corrupt strings that contain spaces. This tends to make the engine less crashy.

**Runtime Randomization**\
Makes a new random string each time the corrupted code is ran. Only works with Nightmare mode and One per line mode.

**Replaces:** 1 instruction\
**Creates:** Runtime randomization off: 1 instruction. Runtime randomization on: Depends

### Nuker Engine

This engine removes all of the instructions from a method and makes it return a different value. When using this engine, the intensity represents the percentage of methods to corrupt rather than the percentage of instructions.

**Byte/Short/Int/Long/Float/Double**\
Pick a random number between the minimum and maximum and return that value. When "Runtime Randomization" is checked, the corrupted code will return a different random value each time it runs.

**Char**\
Pick a random character from the text box. When "Runtime Randomization" is checked, the corrupted code will return a different random character each time it runs.

**Bool**\
Return true or false, or pick randomly, depending which you have checked. When "Runtime Randomization" is checked, the corrupted code will pick randomly each time it runs.

**Void**\
Removes all of the code. Voids return nothing. Checking "Skip static class initializers" and "Skip class initializers/constructors" will cause the game to crash less often.

**String**\
Return a random string. If 'charset' is selected, it will return a string made of random characters from the text box that is as many characters long as the button says. If "one per line" is selected, one random line of text will be chosen. When "Runtime Randomization" is checked, a new string will be randomly selected/generated each time the corrupted code runs.

**Replaces:** 1 instruction\
**Creates:** 1 instruction
