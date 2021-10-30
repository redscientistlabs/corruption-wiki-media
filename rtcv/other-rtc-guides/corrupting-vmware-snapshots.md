---
description: Safely destroying operating systems using Virtual Machines
---

# Corrupting VMware snapshots

**Guide written by:**_ _Modnark\
__**Software used in guide:** RTCV, FileStub,VMware Workstation 16__

### WARNING: **This is a community-made guide for corrupting Operating Systems (windows,mac,linux) by blasting a VMware snapshot using FileStub. This is not a magic technique for windows destruction, you have to play around with it and results may vary from a system to another. Thank you for understanding.**

How to corrupt virtual machine snapshots

What you need:

* VMware Workstation, this guide was made using VMware Workstation 16, as far as I know the version does not matter.
* A virtual machine that has an operating system installed. If you do not know how to do this, please refer to this page: https://www.sysnettechsolutions.com/en/install-windows-xp-vmware/

Notice:

* If you have VMware installed, it is necessary that you know the directory where you are storing VMs in. This can be found by clicking Edit > Preferences, and then look for "Default location for virtual machines". This path indicates where your VMs are stored.
* If the RAM amount is greater than 1GB you may have to disabled caching & multithreading on the file stub by clicking the cog button that sits next to the "Advanced Options" button and then unticking the "Use Caching + Multithreading" option.

With that out of the way, you can now learn how to corrupt virtual machines with VMware and RTCV!

Virtual machine snapshots (at least in VMware) are dumps of memory saved to a file within the directory of a vm. These snapshots can be created by clicking on the button with an icon of a clock with a little orange "+" image. The name specified for the snapshot does not matter.

After clicking "Take Snapshot" you will have to wait for it to finish saving or else you will not be able to load it into the file stub for corrupting. You can see the current status by looking at the bottom left-hand corner of the VMware window.

Once it has finished saving, you can now load it into the file stub by first clicking on the "Browse target" window, which will make a file open dialog appear. Navigate to the aforementioned "Default location for virtual machines", and locate the folder with the same name as you gave the VM. Open up this folder and locate the newest file that has a ".vmem" file extension, and once you've found it, highlight it and click the "Open" button.

Now you should see the path to the file show up inside of the file stub window, and the last step to setting the corrupting up is to click "Load targets into RTCV". Now you're able to corrupt this like anything else, and once you've blasted it you can head back over to VMware and click the button with an orange arrow pointing to the left to load the corrupted snapshot. And voilà! just like that you have now corrupted a VM! Pretty simple eh?

You can get better and more wacky results by creating a VMD that has a range from 0 to some other lower number, possibly a few ten thousand more bytes from 0, and then use said VMD when corrupting. For more information on creating VMDs you can visit this page: https://corrupt.wiki/corruptors/rtc/expert/vmd-generator
