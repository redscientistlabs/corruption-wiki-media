# Scares Scrambler

## &#x20;**Scares Scrambler (v1.21)**

![](<../../.gitbook/assets/image (59).png>)

&#x20;**Author:** Zach “Scares” Strong\
**Source:** [https://github.com/Cocoatwix/Scares-Scrambler-Class-Rebuild](https://github.com/Cocoatwix/Scares-Scrambler-Class-Rebuild)\
**Download:** [https://github.com/Cocoatwix/Scares-Scrambler-Class-Rebuild/releases/tag/v1.22](https://github.com/Cocoatwix/Scares-Scrambler-Class-Rebuild/releases/tag/v1.22)

![](<../../.gitbook/assets/image (30).png>)



#### Index

* [**Index**](scares-scrambler.md#index)
  * [**Functions**](scares-scrambler.md#functions)
  * [**Algorithms**](scares-scrambler.md#algorithms)
    * [Basic Functions](scares-scrambler.md#algorithms-basic-functions)
    * [Special Functions](scares-scrambler.md#algorithms-special-functions)
  * [**Corrupt and Repeat**](scares-scrambler.md#corrupt-and-repeat)
  * [**Miscellaneous**](scares-scrambler.md#miscellaneous)
  * [**Example Preset**](scares-scrambler.md#example-preset)
  * [**Video Tutorial**](scares-scrambler.md#video-tutorial)
  * [**Feedback**](scares-scrambler.md#feedback)



### **Functions**

File - Choose File (Alt+F)

![](<../../.gitbook/assets/image (25).png>)

This window is used to choose the desired file to corrupt, as well as the name and location for the resulting corrupted file. “Select File” will open a standard dialogue box for selecting the file to corrupt. “Select Folder” will open a custom window for selecting a folder or specific file for the resulting corrupted file (see below). Alternatively, clicking the textbox labelled “Enter new file name…” will let the user enter the file path for the new file manually. “Apply” will set the file to corrupt and the resulting corrupted file to the given values.

If no filename or filepath is given, the corrupted file will default to the name “CorruptedFile”, with the file extension given by the file that’s being corrupted. The file will be placed in the same folder as the Scares Scrambler.

If a filepath is given, but no filename, the corrupted file will be given no name, with the file extension given by the file that’s being corrupted. This is considered a bug and will be fixed in future releases. The file will be placed in the given filepath.

File – Choose File - Select Folder

![](<../../.gitbook/assets/image (37).png>)

This window is used to select a specific filepath for the resulting corrupted file, without the need for typing it manually. This window will be replaced with a more standard dialogue box in future releases. The window contains the current filepath (in this example, it’s “C:/Example\”), the contents of the current folder, and three buttons.

Clicking on the name of any file/folder in the list will select it. Clicking “Ok” will use the current filepath displayed in the window as the filepath for the resulting corrupted file. “Select Folder” will change the filepath to inside the selected folder. “Go Up” will change the filepath to the parent folder of the current filepath. Currently, “Go Up” is slightly bugged and will be fixed in future releases.

File - Save Presets (Alt+S)

![](<../../.gitbook/assets/image (46).png>)

This window is used to save the current settings for the current algorithm to a simple text file. Entering a filename into the textbox and clicking “Ok” will save a preset file to the same folder as the Scares Scrambler.

File - Load Presets (Alt+L)

Opens a standard dialogue box to select a preset file. Once selected, the settings from the preset file will be applied to the Scares Scrambler.

Options – Hexadecimal Mode

Turning this on will allow the user to use hexadecimal values for all number inputs within the Scares Scrambler. Toggling this option will automatically convert any numbers already inputted into the corrupter into their respective hexadecimal representations, or back into decimal.

Options – Auto Insert Auto End

Turning this option on will allow the corrupter to automatically insert the chosen file’s size (in bytes) into the corrupter’s “End Value” parameter when choosing new files to corrupt.

Options – Hide File Labels

Turning this on will hide any filepaths/filenames on the main Scares Scrambler window.

Themes

The Scares Scrambler contains three different themes to use: “Light” (Default), “Dark”, and “Dubby”. Each theme changes the corrupter’s logo and colours. To change between them, simply click the desired theme in the Themes menu.

About – Info (Alt+I)

Displays some basic info about the Scares Scrambler.

About – Contributors

Displays a list of project contributors, as well as what they contributed to the project.



### **Algorithms**

Algorithms are the different methods which the Scares Scrambler uses to corrupt files. Certain algorithms are better suited for different filetypes. To switch between different algorithms, click the “…” button below the Scares Scrambler banner and select the desired algorithm.

#### **Algorithms – Basic Functions**

![](<../../.gitbook/assets/image (45).png>)

To change any of the values listed below, simply click the textboxes beside each label and enter the desired value.

Start Value

The Start Value tells the corrupter at which byte of the selected file to start corrupting. This allows the corrupter to leave data near the start of the file uncorrupted.

End Value

The End Value tells the corrupter at which byte of the selected file to stop corrupting. This allows the corrupter to leave data near the end of the file uncorrupted.

Inc Value

The Inc Value tells the corrupter how much to add/subtract to a certain value whenever a “+/-” button is clicked. For example, setting the Inc Value to 20, then clicking the “+/-” button beside the Start Value will add 20 to the Start Value. Right-clicking the “+/-” button will subtract 20.

“+/-” Button

Whenever a “+/-” Button is clicked, the Inc Value is added to the chosen value (the one beside the “+/-” Button). Whenever a “+/-” Button is right-clicked, the Inc Value is subtracted from the chosen value.

Auto End

The Auto End button will insert the selected file’s size (in bytes) into the End Value.

Block Size

The Block Size tells the corrupter the size of the corrupted blocks. In other words, it tells the corrupter how many bytes to corrupt in a row, without leaving a space. Each algorithm uses this value differently. Check each algorithm’s description for specific details.

Block Space (Exponent/Upper Bound)

The Block Space tells the corrupter how much uncorrupted space to leave between corrupted blocks (groups of corrupted bytes). Below this value are three radiobuttons labelled “Linear”, “Exponential”, and “Random”. These buttons give the corrupter different ways to leave uncorrupted space.

Linear

Linear is the default option selected. Selecting Linear tells the corrupter to leave a specific amount of space between each corrupted block. That specific amount is determined by the value of Block Space.

Exponential

Selecting Exponential tells the corrupter to leave an increasing amount of space between each corrupted block. The maximum spacing between corrupted blocks is capped at one million (1000000). Exponential is the only value in the Scares Scrambler where a fractional value can be used (1.2, 12.456, etc.). This setting changes “Block Space” into “Exponent”. The exact formula used to determine the space between corrupted blocks is x^(Exponent), where Exponent is the value of Exponent, and x is an integer which gets incremented by 1 for each corrupted block. The initial value of x is 1.

Random

Selecting Random tells the corrupter to leave a random amount of space between each corrupted block. This setting changes “Block Space” into “Upper Bound”. The value of Upper Bound tells the corrupter the highest possible space between corrupted bytes; it limits how high the spacing can be.

Random Buttons

Clicking the Random Buttons situated beside certain values will give a random number between 0 and 255, inclusive, to that value.

#### **Algorithms – Special Functions**

Incrementer Algorithm

The Incrementer Algorithm adds a specific amount to each byte it corrupts. If the value of the byte exceeds 255, its value will be divided by 255, and the remainder of that division will be used instead.

Incrementer Algorithm – Add/Subtract

The Add/Subtract value is the specific amount that the Incrementer Algorithm adds to each byte. This value can be negative.

Randomizer Algorithm

The Randomizer Algorithm sets every byte it corrupts to a random value between 0 and 255, inclusive.

Scrambler Algorithm

The Scrambler Algorithm takes two blocks (groups of bytes) and swaps them. In other words, the first block will be placed where the second block is, and vice versa. The exact size of these blocks is determined by the value of Block Size.

Scrambler Algorithm – Block Gap

The Block Gap determines the space between the blocks which get swapped. This value is different from Block Space, which determines how much uncorrupted space to leave between pairs of corrupted blocks.

![](<../../.gitbook/assets/image (17).png>)

Copier Algorithm

The Copier Algorithm takes a block (group of bytes) and copies it to a second block. The exact size of these blocks is determined by the value of Block Size.

Copier Algorithm – Block Gap

The Block Gap determines the space between the original block and the copied block. If this value is positive, the first block will be copied to the second block. If this value is negative, the second block will be copied to the first block. Essentially, whether the Block Gap is positive or negative will determine the direction in which the data is copied. This value is different from Block Space, which determines how much uncorrupted space to leave between pairs of corrupted blocks.

Tilter Algorithm

The Tilter Algorithm will replace each corrupted byte with a specific value.

Tilter Algorithm – Replace

The Replace value tells the corrupter which byte values to replace. In other words, the Tilter Algorithm will only replace bytes that have the same value as Replace. This value only takes effect when “Exclusive” is checked.

Tilter Algorithm – Replace With

The Replace With value tells the Tilter Algorithm which value to replace corrupted bytes with.

Tilter Algorithm – Exclusive

If the Exclusive checkbox is checked, the Tilter Algorithm will only replace bytes within the blocks (groups of bytes) that match the value of Replace. If the Exclusive checkbox is unchecked, the Tilter Algorithm will replace every byte within the corrupted blocks.

Smoother Algorithm

The Smoother Algorithm replaces bytes with the average of all the bytes in the corrupted block (groups of corrupted bytes) pair.

Smoother Algorithm – Block Gap

The Block Gap tells the Smoother Algorithm how much space to leave between the original block and the smoothed block. If this value is positive, the second block will be corrupted. If this value is negative, the first block will be corrupted. Essentially, whether this value is positive or negative will determine which block in each pair will be corrupted. This value is different from Block Space, which tells the Smoother Algorithm how much space to leave between pairs of corrupted blocks.

Smoother Algorithm – Termwise

If Termwise is checked, each byte in the corrupted block will be replaced with the average between itself and the byte in the same relative position in the other block. If Termwise is unchecked, each byte in the corrupted block will be replaced with the average of all the bytes within the corrupted block and the other block.

Blender Algorithm

The Blender Algorithm takes two files and blends them together, forming one corrupted file. Essentially, blocks (groups of bytes) will be copied from one file to another, according to the values of Block Size and Block Space.

Blender Algorithm - File Offset

The File Offset determines where in the secondary file to start copying bytes from. It’s essentially another Start Value for the secondary file.

Blender Algorithm – Select File

The Select File button opens a standard dialogue box to select a secondary file to corrupt with. It chooses the file to blend with the chosen file.

### **Corrupt and Repeat**

![](<../../.gitbook/assets/image (69).png>)

The Corrupt and Repeat feature allows the user to create multiple corrupted files at once. To open Corrupt and Repeat, click the “Corrupt and Repeat” button below the “Corrupt” button on the main window.

Corrupt and Repeat – Basic Usage

Depending on which algorithm you select, the Corrupt and Repeat window will have different parameters to change. Each parameter will be tied to a parameter of the chosen algorithm. For example, the above screenshot shows a Corrupt and Repeat window for the Incrementer Algorithm.

To use the Corrupt and Repeat window, simply enter the number of files you’d like to create in the “Number of Files” textbox, then adjust the “Inc” values. The first corrupted file will use the values given in the main Scares Scrambler window for corrupting. Every subsequent file created will add the “Inc” values in the Corrupt and Repeat window to the values given in the main window and use those for corrupting.

For example, setting “Start Value Inc” to 1 will increase the Start Value by 1 for each new file created.

Corrupt and Repeat – Store files in new folder

If this option is checked, all the corrupted files will be placed in a new folder located in the filepath specified in the “Choose File” window. If this option is unchecked, all the corrupted files will be placed directly into the filepath specified. Note: this option may not behave properly if no filename/filepath is given.

### **Miscellaneous**

Auto-Load Presets

The Scares Scrambler automatically searches for preset files on startup. If a preset file is found in the same folder as the Scares Scrambler, then it will auto-load its settings.

Different Preset Versions

Currently, there are two preset formats: “preset” and “preset16”. “preset” was used with Scares Scrambler (v1.1), while “preset16” is used in the current version (v1.21). Both presets will work but be warned that in future versions the corrupter may drop support for older preset types.

A Note on Files

The Scares Scrambler comes with a few Python files and images. The corrupter needs these files in order to function, so uh, don’t remove them thanks!!!

### **Example Preset**

{% file src="../../.gitbook/assets/good-fearful-harmony-intro.txt" %}
Example Preset for a PSX Bios Corruption
{% endfile %}

It takes in the Playstation BIOS file “scph1001.BIN” and spits out “Corruptedscph1001.BIN”. The corruption is of one of the corruptions I got in the Playstation BIOS Corruptions #3 video. Tested on ePSXe200 v2.0.0.

### **Video Tutorial**

[https://www.youtube.com/watch?v=MOQykOsMeEU](https://www.youtube.com/watch?v=MOQykOsMeEU) (made for v1.1, but still applicable)

### **Feedback**

Any feedback on the corrupter can be sent via a comment to this YouTube channel: [https://www.youtube.com/user/scares009](https://www.youtube.com/user/scares009)
