# The Blast Generator

The Blast Generator is a tool which acts similar to classic style ROM corruptors. You can use the Blast Generator to create blastunits.

##### Type

The blastunit type to generate

##### Mode

The mode for generation

##### Step Size

How many addresses to "step" in between generated blastunits.

##### Start Address

The address to start corruption generation at

##### End Address

The address to end corruption generation at.

##### Param1

A parameter for the corruption generation. See below for details on how it's used.

##### Param2

A parameter for the corruption generation. See below for details on how it's used.





Endianess is always handled as little endian, or right -&gt; left. This is completely agnostic of core endianess

That means that:

10 on 16-bit precision will be treated as 00 10

1000 on 16-bit precision will be treated as 10 00



Ranges are exclusive, meaning that the last address is excluded from the range.

This means that:

Start Address of 10, End address of 16, step size of 1 would generate blasts for addresses 10,11,12,13,14,15

## Modes

### BlastByte

##### SET

Sets an address to a specific value.

Param1: The value to set to  
Param2: Unused

##### ADD

Adds a value to the value at the address selected.

Param1: The value to add  
Param2: Unused

##### SUBTRACT

Subtracts a value from the value at the address selected.

Param1: The value to subtract  
Param2: Unused

##### SHIFT\_RIGHT

Copies a value from the selected address a set number of bytes to the right

Param1: How many bytes over you want to shift  
Param2: Unused

##### SHIFT\_LEFT

Copies a value from the selected address a set number of bytes to the right

Param1: How many bytes over you want to shift  
Param2: Unused

##### RANDOM

Sets the value at the address to a random value.

Param1: Unused  
Param2: Unused

##### RANDOM\_RANGE

Sets the value at the address to a random value within the range provided.

Param1: The lowest possible value  
Param2: The maximum possible value

##### REPLACE\_X\_WITH\_Y

Replaces a value with another if the value matches the parameter.

Param1: The value to search for  
Param2: The value to replace with.

##### BITWISE\_AND

Performs a Bitwise AND on the value and a parameter

Param1: The value to perform the bitwise operation with.  
Param2: Unused

##### BITWISE\_OR

Performs a Bitwise OR on the value and a parameter

Param1: The value to perform the bitwise operation with.  
Param2: Unused

##### BITWISE\_XOR

Performs a Bitwise XOR on the value and a parameter

Param1: The value to perform the bitwise operation with.  
Param2: Unused

##### BITWISE\_COMPLEMENT

Performs a Bitwise complement on the value and a parameter

Param1: The value to perform the bitwise operation with.  
Param2: Unused

##### BITWISE\_SHIFT\_LEFT

Performs a Bitwise Left Shift on the value

Param1: How far to shift left  
Param2: Unused

##### BITWISE\_SHIFT\_RIGHT

Performs a Bitwise Right Shift on the value

Param1: How far to shift right  
Param2: Unused

##### BITWISE\_ROTATE\_LEFT

Performs a Bitwise Left Rotation \(cyclical shift\) on the value

Param1: How far to rotate left  
Param2: Unused

##### BITWISE\_ROTATE\_RIGHT

Performs a Bitwise Right Rotation \(cyclical shift\) on the value

Param1: How far to rotate left  
Param2: Unused

### BlastCheat

See BlastByte

Additional modes:

##### FREEZE

Freezes a value at the stepped address to its current value.

Param1: Unused  
Param2: Unused

### BlastPipe

##### Chained

Generates chained pipes.

Param1: Unused  
Param2: Unused

##### SOURCE\_RANDOM

Sets the source address as something random with the destination address being the stepped address

Param1: Unused  
Param2: Unused

##### SOURCE\_SET

Sets the source address as something set with the destination address being the stepped address

Param1: Address to set the source to  
Param2: Unused

##### DEST\_RANDOM

Sets the source address as the stepped address with the destination being something random

Param1: Unused  
Param2: Unused

Additional details on Bitwise Operations can be found here:

[https://en.wikipedia.org/wiki/Bitwise\_operation](https://legacy.gitbook.com/book/x8bitrain/corrupt-wiki/edit#)

