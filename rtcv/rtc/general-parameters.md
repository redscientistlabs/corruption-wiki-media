# General Parameters

### Auto-Corrupt

When this is enabled, RTC will attempt to Generate and Execute a [BlastLayer](concepts-and-vocabulary.md#blastlayer) on every [Emulation Step](concepts-and-vocabulary.md#emulation-step). The amount of corruption can be set by changing the [Intensity](general-parameters.md#intensity) and [Error Delay](general-parameters.md#error-delay) settings.

### Manual Blast

_Alternatively to_ [_Auto-Corrupt_](general-parameters.md#auto-corrupt)_, Blasting a game with corruption can be triggered manually._

Blasts with a bigger [Intensity ](general-parameters.md#intensity)can be as effective as a controlled stream of corruption. It does give the user more control on when the game is altered.

### Error Delay

_Only Applicable to_ [_Auto-Corrupt_](concepts-and-vocabulary.md#auto-corrupt)_._

The Error Delay is a divider to the amount of generated corruption. This defines Auto-Corrupt will Blast the game every X [steps](concepts-and-vocabulary.md#emulation-step).

_Example of how generation works with Error Delay:_\
_1 second @ 60fps with Intensity 500 and Error Delay 1 will generate 30k units_\
_1 second @ 60fps with Intensity 30k and Error Delay 60 will generate 30k units._\
_The difference is that the first one will generate a constant stream of units while the second one will generate a big block of units every second._

_It should be worth noting that tweaking the Error Delay is NOT necessary to get corruption results. It only serves as a way to space out blasts during auto-corrupt._

### Intensity

The Intensity is a multiplier to the amount of generated [Units ](concepts-and-vocabulary.md#blastunit)in a [Blast](concepts-and-vocabulary.md#blast)

_Generally, the higher the Intensity is, the more corruption will happen_

Some [engines ](corruption-engines.md)generate [Active Units](concepts-and-vocabulary.md#active-and-infinite-units), which execute code on every frame that they are active. There is a maximum amount of 50 active units by default. This setting can be changed in the engine settings (when applicable) or in Settings and tools -> Corruption Settings

_This means that a Blast with 100 Intensity while Max Active Units is set to 50 will have the same result as a blast with 50 intensity, given that the currently selected engine generates Active Units._

### Blast Radius

When a Blast is generated, RTC can target multiple [Memory Domains](concepts-and-vocabulary.md#memory-domain) at once. Changing the Blast Radius affects how corruption scatters across the selected Memory Domains.

Spread: Randomly spread across the Memory Domains.

Chunk: Sent to a single zone that is randomly selected among the selected Memory Domains.

Burst: 10 Chunks of 1/10 of the total Intensity.

Even: Apply the blasts evenly spread through all selected domains.

Proportional: Apply the blasts proportionally through all selected domains based on the sizes.

Normalized: Iterate through all selected domains and apply blasts of intensity / (size of largest domain / size of current domain)

###
