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

{% embed url="https://www.youtube.com/watch?v=VKrP0NnGU78" %}
Video Tutorial
{% endembed %}

1. Install FileStub from the RTC Launcher
2. Open the package downloader from the RTC Launcher.
3. Click PLUGINS, then scroll down and click on the Java Corruptor package. The package downloader might crash while downloading it. If that happens, just try again.
4. Create a new installation in the Minecraft launcher with the version that you want to corrupt.
5. Open FileStub and select "Minecraft Version : version.jar" under Target Type.
6. Select your Minecraft version and username of choice in the menu, then click "Load targets into RTCV" at the bottom right.
7. In RTC's main window, click "Custom Layouts" on the left and select "Load Java Corruptor."

You can now read this guide or watch the video in it to learn how to create corruptions for the game.

{% content-ref url="java-corruptor-plugin.md" %}
[java-corruptor-plugin.md](java-corruptor-plugin.md)
{% endcontent-ref %}





{% hint style="warning" %}
The following methods are significantly less efficient than using the official Minecraft launcher with the FileStub template.
{% endhint %}

## Prism Launcher

1. Install FileStub from the RTC Launcher
2. Open the package downloader from the RTC Launcher.
3. Click PLUGINS, then scroll down and click on the Java Corruptor package. The package downloader might crash while downloading it. If that happens, just try again.
4. Create a new instance in the Prism launcher with the version that you want to corrupt.
5. Launch that instance once to download the game's files.
6. Go to %AppData%\PrismLauncher\libraries\com\mojang\minecraft\\(version)
7. Open the `.jar` file in 7-Zip or WinRAR. If you have neither, install 7-Zip.
8. Enter the `META_INF` folder and delete `MOJANGCS.SF` and `MOJANGCS.RSA` (or two similarly-named files) and close 7-Zip or WinRAR.
9. Open FileStub and drag your `.jar` file into the box labeled "Quick Load drag and drop zone."
10. In RTC's main window, click "Custom Layouts" on the left and select "Load Java Corruptor."
11. Select your engine settings, then click the corrupt button under Blast Tools. Do not click the corrupt button on the far left.
12. There will be a new `.jar` file with a long name in the version folder. In Prism launcher right-click your instance and click edit. Go to the version tab and click "Replace Minecraft.jar." Go to the same path as in step 6 and add the new corrupted `.jar` file.
13. Launch your corrupted Minecraft instance from the launcher. Your game will be corrupted. Whenever you make a corruption, a new `.jar` file will be created, and you will have to replace the Minecraft.jar each time.

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
11. Select your engine settings, then click the corrupt button under Blast Tools. Do not click the corrupt button on the far left.
12. There will be a new `.jar` file with a long name in the version folder. In MultiMC right-click your instance and click "edit instance." Go to the version tab and click "Replace Minecraft.jar." Go to the same path as in step 6 and add the new corrupted `.jar` file.
13. Launch your corrupted Minecraft instance from the launcher. Your game will be corrupted. Whenever you make a corruption, a new `.jar` file will be created, and you will have to replace the Minecraft.jar each time.
