# The Blast Generator

The Blast Generator is a tool which acts similar to classic style ROM corruptors. You can use the Blast Generator to create blastunits 



Endianess is always handled as little endian, or right -&gt; left.This is completely agnostic of core endianess

That means that:

10 on 16-bit precision will be treated as 00 10

1000 on 16-bit precision will be treated as 10 00



Ranges are exclusive, meaning that the last address is excluded from the range.

This means that:

Start Address of 10, End address of 16, step size of 1 would generate blasts for addresses 10,11,12,13,14,15





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

Param1: The value to add

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

##### RANDOM

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

Performs a Bitwise COMPLEMENT on the value and a parameter

Param1: The value to perform the bitwise operation with.

Param2: Unused

##### BITWISE\_SHIFT\_LEFT

##### BITWISE\_SHIFT\_RIGHT

##### BITWISE\_ROTATE\_LEFT

##### BITWISE\_ROTATE\_RIGHT

Additional details on Bitwise Operations can be found here: https://en.wikipedia.org/wiki/Bitwise\_operation

### BlastCheat

### BlastPipe



