# RTCV Dev Startup Guide

This guide covers the standard setup for RTCV Development and the basic things the know for navigating this program. This guide will recommend tools such as Visual Studio and Github Desktop but if you are familiar with alternatives, feel free to use them. Just keep in mind that you could encounter issues that we haven't.

Here's the programs that we will use:

* Microsoft Visual Studio 2022 (Community Edition)
* Github Desktop

## Visual Studio installation

If you haven't installed Visual Studio yet, you can grab the community edition from free on microsoft's visualstudio.com website. The 2022 version is the once we currently work with, but 2019 will most likely work too. VS Code is also an alternative if you're into that.

[https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com/)

For the Visual Studio installation, you will need the ".NET desktop environment" in the Installer components. I usually also throw in "ASP.NET" and "Universal Windows Platform" with it but that's not required for RTCV development.

![](<../../.gitbook/assets/image (67).png>)

## Getting the source code

This part of the guide will use Github Desktop as the git client. If you've never played with git before (or if you're tired of complicated git interfaces), you will want to give Github Desktop a try.&#x20;

[https://desktop.github.com/](https://desktop.github.com/)

You will now need to clone the following repositories for a base development platform:

RTCV : [https://github.com/redscientistlabs/RTCV/](https://github.com/redscientistlabs/RTCV/)

Bizhawk50X-Vanguard: [https://github.com/redscientistlabs/Bizhawk50X-Vanguard](https://github.com/redscientistlabs/Bizhawk50X-Vanguard)

_**"Where do i put those repositories?"**_

So, you could technically put these anywhere you want. Visual Studio likes to create repositories in C:\Users\\\[username]\sources. Some people like to have project folders a the roof of their C drive.

I personally prefer creating a PROJECTS folder in my documents and put all the repositories in there. What's important is that whenever you clone a repository for use with RTCV, you have to keep them side by side. For example, the RTCV folder and the Bizhawk50X-Vanguard folder would have to sit in the same folder. If you were to add plugins, they would also have to sit in that same folder level.

Using the Clone repository function, get those two folders side by side in the project folder.

![](<../../.gitbook/assets/image (64).png>)

Then, go back to the RTCV repo in Github Desktop and switch to the branch 51X ~~506v2~~. This is the current branch we use for final the 5.1.x dev .\


![](<../../.gitbook/assets/image (79).png>)

Usually, the main branch for emulators and plugins will be master, with ocasionally the "Vanguard" branch in certain emulators. This guide will not cover the setup for any other emulator than Bizhawk50X. This version of Bizhawk is currently our modded emulator of choice for testing plugins and new features. The reason being that it is in a detached repository that is not tailored to any external development (such as most of our emulator forks).

## Preparing the MegaSolution

RTCV is designed to be modular and expanded via many things such as lists, plugins and custom layouts. The program, in its entirety is so massive that any new feature that isn't deemed "essential" to the base user has to be isolated in a plugin to prevent the program from over-inflating.

During general QA testing of the application, it is recommended to load as many Plugins as possible in order to trap various edge cases related to plugin interaction. This however is very expansive in terms of cpu and memory usage and can't be recommended for casual development.

_SLN file: ..\Bizhawk50X-Vanguard\Real-Time Corruptor\BizHawk\_RTC\RTCV\_MegaSolution.sln_

The MegaSolution will most likely not fully load when you open it. Not just because of the amount of plugins and projects that your Visual Studio is not going to be able to load, but due to the nuget packages having to be refreshed.

![](<../../.gitbook/assets/image (61).png>)

Once you're done setting all of this, you can delete the links to the missing projects if you want to get rid of errors on startup (Not now, do it once it all works). Everything that isn't included in RTCV and Bizhawk50X is non-essential.

![](<../../.gitbook/assets/image (73).png>)

It seems like in Visual Studio 2022, the MegaSolution can sometimes fail to refresh the nuget packages correctly, we'll have to fix that if you have the error shown above.

Open the Package Manager Console with Tools -­> Nuget Package Manager -> Open Package Manager Console

![](<../../.gitbook/assets/image (74).png>)

_In the console, type the following command: Update-Package -reinstall_

This will force-reinstall all nuget packages from their original repos. This can take a few minutes. Once this is all done, the console will go back to PM­>

Try building the solution like that

![](<../../.gitbook/assets/image (66).png>)

The first time it compiles, it might take some time and even throw errors. The compilation progress bar looks like this:

![](<../../.gitbook/assets/image (70).png>)

If it fails, do not do a Rebuild. Keep going for Build solution again and see if it succeeds.

![](<../../.gitbook/assets/image (60).png>)

If after a few builds it still doesn't fully compile, check the Error List and Output tabs to get a clue of what's going on. Probably a nuget package not working or something. These are a mess sometimes.

## Preparing for a dual process Debug

In the Solution Explorer (usually on the right), right click on the top icon of the solution tree (usually the purple one) and go in the properties of the solution.

Here, you will want to switch your startup project to Multiple startup projects.

_Find Bizhawk.Client.EmuHawk and set it to Star_t

_Find StandaloneRTC and set it to Start_

Press OK to save and click the Start icon to boot RTCV in debug mode

![](<../../.gitbook/assets/image (75).png>)

You should now have RTCV and Bizhawk starting up and connecting to eachother.

## Particularities of Debug mode

Running any program in Debug mode inherently makes it slower. This is because everything is unoptimized in order for the debugger to break and give correct debug information to the developer. The RTCV interface is a bit slower but the first thing you'll notice is that emulation is also much slower in debug mode. I have found the QuickNes is works fairly well in debug mode so if you're just testing RTCV stuff and need performance, keep it to Nes emulation.

By default, the Auto-Killswitch will not fire in Debug mode if a debugger is attached. If you need to test a situation where the Killswitch might trigger, either run without the debugger attached or hook to StandaloneRTC after the emulator crash/restart (or just replace Debugger.IsAttached with true in the Killswitch module).

In any case, it should be worth also mentioning that if your emulator crashes and gets restarted with the Killswitch, Visual Studio will not reattach to it automatically. You will need to go to the menu Debug -> Attach to process... in order to reattach to the emulator.

Also keep in mind that non-managed emulators (c++ based ones) are much harder to debug than BizHawk, it being mostly developed in C#.

## Navigating NetCore Routing

This could be a topic on its own but if you're debugging RTCV, you need to understand about how data and function calls is running between processes. Our communication method is an UDP+TCP RPC system we call NetCore2 which allows synchronous and asynchronous calls between processes.&#x20;

This means that a sync call between the process will lock the caller's thread automatically until the message returns. This could be dangerous process as it would could be a cause for deadlocks if the RPC ran on the main thread, but in the case of NetCore2, it is not. Both processes run NetCore on a separate thread and it is possible to invoke the Form thread in a way that does not deadlock the system even with two sync calls fired both ways at the same time.

Take the following call for example:

```
LocalNetCoreRouter.QueryRoute(NetCore.Endpoints.CorruptCore, NetCore.Commands.Remote.SaveState, sk);
```

This call is a Query, meaning that it is automatically Synced (although the function does support it not being synced but the return value will need to be caught some other way.

The first parameter \[NetCore.Endpoints.CorruptCore] of the QueryRoute or Route function contains a string-enum that specifies which endpoint is expected to receive the call.&#x20;

Every endpoint except for Vanguard will be routed within the StandaloneRTC process, Vanguard will be routed to the Emulator process and will fallback to CorruptCore within the Emu process if Vanguard didn't have a definition for the command.

\[RTCV.NetCore.Commands.Remote.SetApplyCorruptBL] is a string-enum that specifies which command is being sent. Each endpoint the registers to the local router is expected to handle those commands or reject/ignore them. Check out the Connector source files for more info on that.

"sk" is the object payload send through the call router. It can be anything, but must be serializable if it goes through processes. in this case, sk is a StashKey object, which represents a complete corruption item (metadata, savestate id and blastlayer).

_**"How do I follow a NetCore call through the program while debugging?"**_

![](<../../.gitbook/assets/image (63).png>)

First of all, you don't want to go step-by-step through NetCore. This is wayyy too many abstraction layers to go through. Instead, you'll want to find the destination using the string-enum. Right-click on the command and do "Find all references".&#x20;

![](<../../.gitbook/assets/image (71).png>)

Chances are that you'll only find a few hits, somewhere in the solution. The one you want is the one that ends in a big switch statement. You can expect your call to land at that point. Put a new break point in the switch case and let the program run. It will break at the other end.

![](<../../.gitbook/assets/image (78).png>)

Now that you're on the other side, you can follow the code whether it's in the Emulator process or in the RTCV Process. Keep in mind that if you're hooked to another emulator that is not running in debug mode, your breakpoint will not fire. Also if you are debugging with another emulator in a separate solution, you need to have the RTCV projects in that other solution otherwise it will also not trigger the breakpoints.

## Inter-process Variable Synchronization

RTCV is designed from the ground up to be running in an unstable environment in which the Emulator process is literally expected to crash.&#x20;

**Emulators crashing due to corruption is inevitable**

RTCV stores its mutating variables in a system called UniSpec. This is a system inside NetCore that functions as a replicating dictionary of variables. Each one or multiple variables are modified within an RTCV Spec, the changes are pushed to both processes through a Partial Spec update. This keeps those critical variables synced up across processes.&#x20;

If the emulator crashes and restarts, once it connects to RTCV, it will grab a copy of the latest Specs to get back up to date with the other process. Whenever there's a crash happening, the Cloud Debug info contains dumps of the specs from both processes (when possible). This is really useful for telling exactly what was in the process memory at the moment of a crash.

## Ensuring your code runs on the Main thread from anywhere

At any time in the code, if you're attempting to modify something in the UI from another thread, you will get an error about editing stuff from the wrong thread. Normally, the good practice would be to figure which form holds the handle to the thread and invoking it. We're really lazy so we've wrapped this into an action caller.

```
SyncObjectSingleton.FormExecute(() =>
            {
                // This code will run on the Main thread
                // Which is usually the main form thread
            });
```

Simply by wrapping your code with this snippet will ensure that your code isn't running on the wrong thread. If it gets called twice (a call within the other), it will not deadlock because of how the wrapping is designed. This is always safe to use for quick operations but take note of the following quirk:

When executing code in the Form Thread in the emulator process, this prevents the killswitch from pinging back. This is a normal behavior as this is how we can detect that the emulator has frozen. If you need to process stuff in the emulator process, try to do it with another thread than the main thread if possible.

## Singleton Form System

The RTCV Grid system is too complex for this guide but here's what you need to know:

In the StandaloneRTC process, you can get ahold of a singleton form by calling it with the S object and passing the type&#x20;

```
S.GET<CoreForm>();
```

This gets the form singleton and will initialize it if it hasn't been initialized yet.

Forms that inherit from the ComponentForm class can be anchored in the RTCV UI or be summoned for a Custom Layout.

