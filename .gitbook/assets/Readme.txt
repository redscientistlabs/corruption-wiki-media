Patchinator (Genesis/MD/32x ROM patching tool) by: Tony H
Version 1.0   2/9/2023
For Windows   (written in C#)

Send bug reports or comments to: t_hedstrom@yahoo.com

My site, with other programs, editors, Game Genie codes, etc...
https://codehut.gshi.org/
http://www.angelfire.com/games2/codehut/

Version 0.9 = Initial public release.  2/2/2021
Version 1.0 = Added lots of improvements (listed below).  2/9/2023


Improvements with version 1.0:

Can patch 3 codes at once now, can write your own notes for each of the codes and click a button to save them to a text file along with the codes, addresses, values, and other useful info, can now enter your own ROM addresses and values (instead of just entering Game Genie codes), gives warnings when you use odd numbered ROM addresses since ROM addresses should be even numbers, has much better checksum fixing now including Electronic Arts, Konami, Sega, Capcom, and others, can "Auto-fix" checksums after patching if you'd like, has an option to create a new ROM when patching, shows the size of the ROM and limits the ROM addresses you can enter based on the ROM size, can now patch ROMs up to 14.6 MB (Demons of Asteborg ROM), program no longer uses a separate dll file, has an option to put 32x ROMs into a developer mode, and many other improvements.

 
Patchinator will patch Game Genie or raw codes into any Genesis, Mega Drive, or 32x ROM.  It will also fix checksums for you, including fixing checksum problems with EA (Electronic Arts), Capcom, and many other ROMs.

There are two Help buttoms in the program that should answer any questions.

Version 1.0 no longer requires a dll file.  The C# code for decrypting Game Genie codes is now included within the program, and is heavily based on Rimsky82's dll file.

Can find more info about the version 1.0 update here: https://www.romhacking.net/forum/index.php?topic=36472.0

Shouldn't need any additional files if you're using Windows.  It uses the .net framework.
