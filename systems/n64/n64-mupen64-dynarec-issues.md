# N64 mupen64 dynarec issues

Since the move to Bizhawk 64-bit, the mupen64 core has lost its ability to use "dynarec" for recompiling code dynamically. Dynarec made corruptions much more stable by recompiling illegal instructions to something that was less likely to crash the core.

Because of that, it is recommended to use "Bizhawk Legacy" in the RTC Launcher for searching effects. It is possible to take those effects and move them to the most recent version of Bizhawk but it's not guaranteed that it will work 1:1.

Still, the use of Bizhawk Legacy can help a lot when searching for effects as it is much less prone to crashing with N64 corruptions.
