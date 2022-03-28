---
description: For use on Android devices such as Phones, Tablets, VR Headsets.
---

# Corrupting Android Unity games

**Guide written by:** __ bloqhead\
__**Software used in guide:** RTCV, FileStub, Sidequest, APK Easy Tool, 7zip__

### WARNING: **This guide was written for corrupting games made for the Oculus Quest. The Quest devices run android and support sideloading APKs but this guide could also apply to other Android devices or Android software running on Bluestacks. Thank you for understanding.**



This document aims to cover the process of corrupting Unity Android games. I use 7zip (to extract the apks since they are just renamed zips), APK Easy Tool (to sign the apks with the corrupted content), Sidequest to sideload the signed apks back to the device (Sidequest is made for mainly Oculus Quest usage, however \[in short] it is just adb with a gui so any android device will work) and the latest dev build of RTCV with Filestub. For something to automate this process, other tools may be considered over the ones I use to do this manually. Links to the tools I have used can be found at the bottom of the document.

To start, you need the apk of the game that you want to corrupt. For this example, I am corrupting the Quest port of Beat Saber, so I connect my headset to my pc over cable. This is the same process for android phones, just connect it to your pc with a cable. Just to note that for android phones, you may need to enable Developer mode, developer mode is required for Oculus Quest.

Now you need to grab the apk. With your android device connected to your pc, open sidequest and click on the icon with the 9 small squares. It should show a list of all of the apps installed on the device. Now you need to find your game, either scroll down until you see it, or type it’s name in the Search Package box, but keep in mind this searches for app package names and not their actual names (for example Beat Saber is com.beatgames.beatsaber). Once you have found your game, click on it’s cog on the right hand side, and it should pull up a menu. Scroll down and you will see a button labeled “Backup APK File”. Click this, and a after a while the apk will be saved to C:\Users\usernamehere\AppData\Roaming\SideQuest\backups\packagenamehere\apks (obviously usernamehere will be your windows username and packagenamehere will be your app package name). Inside this folder, there will be an apk which has the date it was “backed up” to your pc and at the end, the app version number. With 7zip, right click this apk then select 7zip -> Extract files. Click OK on the 7zip prompt that shows up

You’ll now have a folder with the same name as the apk, with the apk contents inside of it. Open RTCV and then open Filestub. Click on the target type box and select Multiple files (One domain). Then click on the Add button in the Select Multiple Files window, then navigate to your folder with the apk contents. Since Beat Saber is a Unity game, you’ll need to navigate to assets\bin\Data. Select all of the files there (the other folders in Data are excluded) and click Open. Then click “Load Multiple Files in Filestub”, then click Load Targets into RTCV. The main RTC window will now have a domain titled “Multiple files”.

This is where the fun stuff begins.

First, change your Corruption Engine to the Vector engine. This is absolutely required as any other engine will only cause crashes or nothing will happen.

Changing the limiter and value lists are completely optional, so I will be sticking with the standard Extended lists. If you want to obliterate the game right off the bat, crank the intensity super high then click Corrupt. To stack corruptions, you can press “Bake All Dirty” in the filestub window every time you corrupt the files. If you want minimal corruptions, try setting the intensity low.

Once you’ve done corrupting the files to your liking, navigate to the root of the game folder, drag click and select them all, then click 7zip -> Add to foldername.zip. Rename to the extension to .apk, then open APK Easy Tool. Drag and drop the apk onto the “Sign APK” button, and after a while another apk will be produced, with the same name as the og one but with “signed” added onto the end of it. This apk may have a different file size to the og one, but this is nothing to worry about as this is completely normal.

Now it’s time to sideload this signed apk back over to your android device. With sidequest still on the Installed apps tab, click the cog on your selected app again and click Uninstall App. Then drag the signed apk over to the sidequest window, which should cause it to install the apk. After a while a green notification should pop up saying “Task Completed!”. You can now safely disconnect your android device. When you open your now corrupted game, you should see corrupted assets. These can vary from a lot of things, such as models, Text assets and much, much more.

Links: 7zip: https://www.7-zip.org/&#x20;

Sidequest: https://sidequestvr.com/setup-howto&#x20;

APK Easy Tool: https://forum.xda-developers.com/t/tool-windows-apk-easy-tool-v1-59-2-2021-04-03.3333960/ (links can be found at the bottom of the post)

P.S.: If you’re using alternate apk signing methods you need a signing key to sign them!
