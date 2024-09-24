---
description: Plugin and Guide made by NoSkillPureAndy
---

# Corrupting Minecraft with the Java Corruptor Plugin and FileStub

{% hint style="info" %}
This guide assumes that you have already read the base guide for the Java Corruptor plugin. If you haven't already, check it out at[ this page](java-corruptor-plugin.md)
{% endhint %}

{% hint style="info" %}
NOTE: If you have no other plugins the Java Corruptor layout will load automatically when clicking "Load Custom Layout". This was not mentioned in the video.
{% endhint %}

## Minecraft Launcher

{% embed url="https://www.youtube.com/watch?v=dqG2TcqVDQQ" %}
Video Tutorial
{% endembed %}

1. Install FileStub from the RTC Launcher
2. Open the package downloader from the RTC Launcher.
3. Click PLUGINS, then scroll down and click on the Java Corruptor package. The package downloader might crash while downloading it. If that happens, just try again.
4. Create a new installation in the Minecraft launcher with the version that you want to corrupt.
5. Launch that installation once to download the game's files.
6. Click on the folder icon to the right of the installation.
7. In the explorer window that opens, open the `versions` folder.
8. Make a copy of the folder with the name of the version that you want to corrupt, and rename it with `_rtc` at the end.
9. Open the folder and rename the `.jar` and `.json` files within to also have `_rtc` at the end of their names.
10. Open the `.jar` file in 7-Zip or WinRAR. If you have neither, install 7-Zip.
11. Enter the `META_INF` folder and delete `MOJANGCS.SF` and `MOJANGCS.RSA`.
12. Make a copy of the `.jar` file and put `_2` at the end of its name, after `_rtc`.
13. Open the `.json` file in Notepad and copy the text.
14. Search "json formatter" in DuckDuckGo and paste the text into the box, then click "Validate JSON."
15. Delete the text that looks like what's highlighted in this screenshot exactly, and add `_rtc` to the end of the version number surrounded by the red rectangle.&#x20;

    <figure><img src="../../.gitbook/assets/Pasted image 20240817174818.png" alt="" width="531"><figcaption></figcaption></figure>
16. Copy the text from the box, paste it back into Notepad, and save the file.
17. Restart the Minecraft launcher.
18. Make a new installation with your selected version ending in `_rtc`.
19. Open FileStub and drag your `.jar` file with the name ending in `_rtc_2` into the box labeled "Quick Load drag and drop zone."
20. In RTC's main window, click "Custom Layouts" on the left and select "Load Java Corruptor."
21. In the top right, underneath Corruption Engine, select Arithmetic Engine from the dropdown.
22. In the two boxes on the right with math operations, select addition, subtraction, and multiplication in both.
23. Click the corrupt button under Blast Tools. Do not click the corrupt button on the far left.
24. There will be a new `.jar` file with a long name in the `_rtc` version's folder. Delete the old `_rtc.jar` file, and rename the new one to the old one's name.
25. Launch your corrupted Minecraft installation from the launcher. Your game will be corrupted. Whenever you make a corruption, a new `.jar` file will be created, and you will have to rename that file to `version_rtc.jar`, replacing the old one each time.

## Prism Launcher

1. Install FileStub from the RTC Launcher
2. Open the package downloader from the RTC Launcher.
3. Click PLUGINS, then scroll down and click on the Java Corruptor package. The package downloader might crash while downloading it. If that happens, just try again.
4. Create a new instance in the Prism launcher with the version that you want to corrupt.
5. Launch that instance once to download the game's files.
6. Go to %AppData%\PrismLauncher\libraries\com\mojang\minecraft\\(version)
7. Open the `.jar` file in 7-Zip or WinRAR. If you have neither, install 7-Zip.
8. Enter the `META_INF` folder and delete `MOJANGCS.SF` and `MOJANGCS.RSA` and close 7-zip or WinRAR.
9. Open FileStub and drag your `.jar` file into the box labeled "Quick Load drag and drop zone."
10. In RTC's main window, click "Custom Layouts" on the left and select "Load Java Corruptor."
11. In the top right, underneath Corruption Engine, select Arithmetic Engine from the dropdown.
12. In the two boxes on the right with math operations, select addition, subtraction, and multiplication in both.
13. Click the corrupt button under Blast Tools. Do not click the corrupt button on the far left.
14. There will be a new `.jar` file with a long name in the version folder. In Prism launcher right-click your instance and click edit. Go to the version tab and click "Replace Minecraft.jar." Go to the same path as in step 6 and add the new corrupted `.jar` file.
15. Launch your corrupted Minecraft instance from the launcher. Your game will be corrupted. Whenever you make a corruption, a new `.jar` file will be created, and you will have to replace the Minecraft.jar each time.

## MultiMC

1. Install FileStub from the RTC Launcher
2. Open the package downloader from the RTC Launcher.
3. Click PLUGINS, then scroll down and click on the Java Corruptor package. The package downloader might crash while downloading it. If that happens, just try again.
4. Create a new instance in MultiMC with the version that you want to corrupt.
5. Launch that instance once to download the game's files.
6. Go to your MultiMC install folder and browse to libraries\com\mojang\minecraft\\(version)
7. Open the `.jar` file in 7-Zip or WinRAR. If you have neither, install 7-Zip.
8. Enter the `META_INF` folder and delete `MOJANGCS.SF` and `MOJANGCS.RSA` and close 7-zip or WinRAR.
9. Open FileStub and drag your `.jar` file into the box labeled "Quick Load drag and drop zone."
10. In RTC's main window, click "Custom Layouts" on the left and select "Load Java Corruptor."
11. In the top right, underneath Corruption Engine, select Arithmetic Engine from the dropdown.
12. In the two boxes on the right with math operations, select addition, subtraction, and multiplication in both.
13. Click the corrupt button under Blast Tools. Do not click the corrupt button on the far left.
14. There will be a new `.jar` file with a long name in the version folder. In MultiMC right-click your instance and click "edit instance." Go to the version tab and click "Replace Minecraft.jar." Go to the same path as in step 6 and add the new corrupted `.jar` file.
15. Launch your corrupted Minecraft instance from the launcher. Your game will be corrupted. Whenever you make a corruption, a new `.jar` file will be created, and you will have to replace the Minecraft.jar each time.
