# Using a real Wiimote with Dolphin

**Guide written by:** __ NoSkillPureAndy\
__**RTC Version used at the time of making this guide:** RTCV 5.0.6__

### **There are 2 parts to this guide. If the first part works, you don't need to do the second part.**

First, you have to connect the Wiimote via bluetooth in control panel. To do so, open control panel. Then click “Hardware and Sound”, “Devices and Printers”, and “Add a device” at the top left. Press 1 and 2 at the same time, or the red button underneath the battery cover and wait for it to include “Nintendo RVL-CNT-01”. When it does, click on it and then click “Next” on the bottom right. Click it again if it tells you to enter a passcode, it doesn’t exist. Wait for it to install what it needs, and you’re done with this step.\


Next, open Dolphin and click “Controllers” in the top right. Change “Emulated Wii Remote” to “Real Wii Remote” in the new menu, and click “Continuous Scanning” below. When you’ve done that, press 1 and 2 at the same time, or the red button underneath the battery cover and then click “Refresh” to the right of that. Click it a few times if it doesn’t work, and wait for it to give you a notification that “Nintendo RVL-CNT-01” is being set up. If this doesn’t happen or it does and your Wiimote continues to flash, you should continue reading. If not, congrats! Your sanity is spared.\
****

## **Only do this next section if your Wiimote did not work with the previous method.**

Next, you need to download **WiimoteHook**. At the time of writing, the official download link\
****[**http://drive.google.com/uc?export=download\&id=123Lq-uX2lwL2Y42iiYi6fUJVwTawiHU9**\
****](http://drive.google.com/uc?export=download\&id=123Lq-uX2lwL2Y42iiYi6fUJVwTawiHU9)found at the bottom of the official guide website



**"**[**https://epigramx.github.io/WiimoteHook/**](https://epigramx.github.io/WiimoteHook/)**"** seems to be non-functional, at the time this guide was written so here's an alternative link via Google Drive:\
****[**https://drive.google.com/file/d/1BOYwYOGaYe6V70k24sMlz1R2cM4zQ6Gg/view?usp=sharing**](https://drive.google.com/file/d/1BOYwYOGaYe6V70k24sMlz1R2cM4zQ6Gg/view?usp=sharing)

**If you have any issues with this guide, you can also try an alternative guide on the WiimoteHook website**

First, unzip the file you downloaded, preferably to your desktop. Open the folder and run “InstallEmulatedGamepadsDriver(run as admin).bat” as administrator. Press any key to continue, and restart your computer. Next, run “WiimoteHook.exe” (not necessarily as an administrator) and press B. When you’ve done that, press 1 and 2 at the same time, or the red button underneath the battery cover and wait for it to discover your WiiMote. If it says it was paired and it’s unpairing, yell at it and try again. Try running it as an administrator, try sacrificing the perfectly good double A batteries from the controller, anything to make it function. You’ll know it’s ready when you get a notification and “USB In” sound effect from your computer, and a bunch of gray text appears in the window. Calibrate the MotionPlus with C on your computer for good luck.\
****

Next, you need to download GlovePIE from here\
****[**https://github.com/Ravbug/GlovePIE/releases/download/Release/GlovePIE-0.45.zip**](https://github.com/Ravbug/GlovePIE/releases/download/Release/GlovePIE-0.45.zip)

and unzip it to your desktop. Run “PIEFree.exe” and paste in this code sample in:\
****

```
key.RepeatMultipleFakeKeys = false
key.W = Wiimote.Nunchuk.JoyY <-0.4
key.S = Wiimote.Nunchuk.JoyY> 0.4
key.A = Wiimote.Nunchuk.JoyX <-0.4
key.D = Wiimote.Nunchuk.JoyX> 0.4

key.Q = Wiimote.A
key.E = Wiimote.B
key.One = Wiimote.One
key.Two = Wiimote.Two
key.Comma = Wiimote.Minus
key.Dot = Wiimote.Plus
key.Enter = Wiimote.Home
key.Up = Wiimote.Up
key.Down = Wiimote.Down
key.Left = Wiimote.Left
key.Right = Wiimote.Right
key.Eight = Wiimote.Shake
//key.Nine = Wiimote.Shake
key.Zero = Wiimote.Shake

key.R = Wiimote.Nunchuk.CButton
key.F = Wiimote.Nunchuk.ZButton

if Wiimote.Pitch < -85 {
   key.G = true
}
if Wiimote.Pitch > -85 {
   key.G = false
}
if Wiimote.Pitch > 85 {
   key.B = true
}
if Wiimote.Pitch < 85 {
   key.B = false
}
if Wiimote.Roll < -55 {
   key.V = true
}
if Wiimote.Roll > -55 {
   key.V = false
}
if Wiimote.Roll > 55 {
   key.N = true
}
if Wiimote.Roll < 55 {
   key.N = false
}

if Wiimote.MotionPlus.PitchSpeed < -800.0 {
   key.K = true
}
if Wiimote.MotionPlus.PitchSpeed < -800.0 and Wiimote.MotionPlus.YawSpeed < -800.0 {
   key.K = true
   key.J = true
}
if Wiimote.MotionPlus.PitchSpeed < -800.0 and Wiimote.MotionPlus.YawSpeed > 800.0 {
   key.K = true
   key.L = true
}
if Wiimote.MotionPlus.PitchSpeed > -800.0 {
   wait 1s
   key.K = false
}
if Wiimote.MotionPlus.PitchSpeed > 800.0 {
   key.I = true
}
if Wiimote.MotionPlus.PitchSpeed > 800.0 and Wiimote.MotionPlus.YawSpeed < -800.0 {
   key.I = true
   key.J = true
}
if Wiimote.MotionPlus.PitchSpeed > 800.0 and Wiimote.MotionPlus.YawSpeed > 800.0 {
   key.I = true
   key.L = true
}
if Wiimote.MotionPlus.PitchSpeed < 800.0 {
   wait 0.5s
   key.I = false
}
if Wiimote.MotionPlus.YawSpeed < -800.0 {
   key.J = true
}
if Wiimote.MotionPlus.YawSpeed > -800.0 {
   wait 0.5s
   key.J = false
}
if Wiimote.MotionPlus.YawSpeed > 800.0 {
   key.L = true
}
if Wiimote.MotionPlus.YawSpeed < 800.0 {
   wait 0.5s
   key.L = false
}

key.U = Wiimote.Stabbing

if Wiimote.DrumBeat == true {
   key.u = false
}

if Wiimote.Nunchuk.Pitch < -45 {
   key.Three = true
}
if Wiimote.Nunchuk.Pitch > -45 {
   key.Three = false
}
if Wiimote.Nunchuk.Roll > 65 {
   key.Four = true
}
if Wiimote.Nunchuk.Roll < 65 {
   key.Four = false
}
if Wiimote.Nunchuk.Roll < -65 {
   key.Five = true
}
if Wiimote.Nunchuk.Roll > -65 {
   key.Five = false
}
if Wiimote.Nunchuk.Roll > 65 {
   key.Six = true
}
if Wiimote.Nunchuk.Roll < 65 {
   key.Six = false
}


```

(Note: This code sample doesn’t support swinging the Nunchuk. Swinging the Wiimote is already janky enough.)\


Next, click “File” in the top left corner and then click “Save As…” in the dropdown. Name it “dolphin wiimote keybinds.PIE” or something to that effect and click “Save” in the bottom right.

Now you have to make the Dolphin settings to work with this. Luckily for you, I’ve already done it. Download this file

[**https://drive.google.com/file/d/1BtVLYKoa1sNDRE9Fb9E9K8Z9JKI\_Kcrj/view?usp=sharing**](https://drive.google.com/file/d/1BtVLYKoa1sNDRE9Fb9E9K8Z9JKI\_Kcrj/view?usp=sharing)

**and put it into your Dolphin configs folder. This can be found here**\
****

\[wherever you put your rtc launcher]\VERSIONS\\\[most recent version, such as RTCV\_5.0.6]\Dolphin\User\Config\Profiles\Wiimote\
****

When you’ve done this, you should now be able to open Dolphin and click “Controllers” in the top right. Change “Real Wii Remote” to “Emulated Wii Remote” in the new menu, and click “Configure” to the right of that. In the top right there should be a section labeled “Profile” with an empty rectangle and downward arrow. Click the downward arrow and select “dolphin pie” from the dropdown. Click “Save” to the right and click “Close” at the bottom right.\
****

Finally, you can now put all that you set up together. Close WiimoteHook and reopen it. Do what you learned previously to get your Wiimote connected to it. Then, press M to enable mouse emulation. Next, go to GlovePIE and click “▶ Run” at the middle top. Now, click onto Dolphin and open whatever game you want. Fullscreen said game, and you should be good to go now. My condolences to your sanity after this.\
