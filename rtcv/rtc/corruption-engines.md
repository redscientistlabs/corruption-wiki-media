# Corruption Engines

_These are the various Engine Templates that you can use for corrupting games. These can be customized in the Custom Engine, in which you can load a template to work from._

### Nightmare Engine

![](<../../.gitbook/assets/image (38).png>)

This engine corrupts on the raw byte level.

_Effect: It changes Bytes in Memory once._

**Blast Type**

This parameter defines the effect applied on Byte(s)

RANDOM: Will replace the Byte(s) at the selected address with random Byte(s)

RANDOMTILT: Will replace the Byte(s) with random Byte(s) or Increments it or Decrements it.

TILT: Will Increment or Decrement random Byte(s).

### Hellgenie Engine

![](<../../.gitbook/assets/image (28).png>)

This engine generate Active Units, which execute on every frame. The Hellgenie Engine replicates the effect of Cheats (see Game Genie, Active Replay, GameShark) and replaces a value with a randomly selected one then applies it on every frame.

Effect: It randomly selects a value and forces a selected address to then keep that value.

**Max Infinite Units**

Infinite Units are resource expensive as they re-write memory on every frame and must be recycled. This allows you to define how many Infinite Units are allowed. New units retire old ones.

**Clear units on rewind**

When enabled, rewinding will clear all [Infinite Units](concepts-and-vocabulary.md#active-and-infinite-units) that have an infinite life time (when applicable).

### Freeze Engine

![](<../../.gitbook/assets/image (48).png>)

This engine generate Active Units, which execute on every frame. The Freeze Engine replicates the effect of Cheats (see Game Genis, Active Replay, GameShark) and replaces a value on every frame. The difference between this engine and the Hellgenie Engine is that this doesn't generate a value but instead keeps the value at the target address and reapplies it on every frame, therefore freezing its value in place.

_Effect: It forces Bytes at a selected address to keep their value._

**Max Infinite Units**

Infinite Units are resource expensive as they re-write memory on every frame and must be recycled. This allows you to define how many Infinite Units are allowed. New units retire old ones.

**Clear units on rewind**

When enabled, rewinding will clear all [Infinite Units](concepts-and-vocabulary.md#active-and-infinite-units) that have an infinite life time (when applicable).

### Distortion Engine

![](<../../.gitbook/assets/image (24).png>)

This engine backups Bytes and restores those backups once, later in time.

_Effect: This corrupts data by restoring parts of it to a previous state._

**Distortion Delay**

This is the amounts of steps that each corruption unit has to wait before restoring a backup.

**Resync Distortion**

This erases all current [active units](concepts-and-vocabulary.md#active-and-infinite-units) pending to be restored.

### Pipe Engine

![](<../../.gitbook/assets/image (25) (2).png>)

This engine generates units that bind addresses together and can make data bleed from a Memory Domain to another. It uses Infinite Units that route memory changes on every Emulator Step or frame.

**Lock Step units**

Prevents any change to be done to the current Active Units

**Clear units on rewind**

When enabled, rewinding will clear all [Infinite Units](concepts-and-vocabulary.md#active-and-infinite-units) that have an infinite life time (when applicable).

### Vector Engine

![](<../../.gitbook/assets/Vector Engine.png>)

This engine corrupts using a Limiter and Value list.

_Effect: Allows for more controlled corruptions via the use of Limiter and Value lists._

**Limiter List**

On the generation of every Unit with this engine, the value at the randomly selected address is going to be compared to a list of legal values called a Limiter List. If the value at the random address isn't legal according to the list, the Unit then will not be part of the BlastLayer.

**Value List**

After generation of the Unit with this engine, a replacement value is assigned to the legal address. This value is randomly selected from a selected Value List.

**Unlock**

Allows the Engine [Precision](corruption-engines.md#engine-precision-and-alignment) to be changed.

#### **Lists**

{% content-ref url="classic-vector-lists.md" %}
[classic-vector-lists.md](classic-vector-lists.md)
{% endcontent-ref %}

### Cluster Engine

<figure><img src="../../.gitbook/assets/Cluster Engine.png" alt=""><figcaption></figcaption></figure>

This engine swaps values with neighboring values.

_Effect: Swaps or rotates values around_

**Limiter List**

On the generation of every Unit with this engine, the value at the randomly selected address is going to be compared to a list of legal values called a Limiter List. If the value at the random address isn't legal according to the list, the Unit then will not be part of the BlastLayer.

**Method**

Changes how the cluster will be picked, based on the main address (can be forwards of backwards)

**Cluster Chunk Size**

Amount of units used in a cluster (total byte size = units X precision)

**Rotate Amount**

How many units of the cluster will be rotated in each execution

**Cluster Direction**

Direction in which the cluster is taken based on the first address

**Split Blast Units**

Will generate single units in the blast editor rather than one big unit for each operation

**Filter All**

Makes the filter check of each units in the cluster rather than just the base address

### Custom Engine

![](<../../.gitbook/assets/image (26).png>)

This engine allows you to mix and match parameters to create your own engine.

Every other engine is in fact just running templates for the Custom Engine. before RTC 5.X, each engine was really its own engine, now they're all living as templates. The parameters you input in here will reflect what you get in the [Blast Editor](blast-editor.md).

### Engine Precision and Alignment

![](<../../.gitbook/assets/image (44).png>)

Allows you to choose what size [BlastUnit ](concepts-and-vocabulary.md#blastunit)will be generated. 8-bit (one byte), 16-bit (2 bytes), 32-bit (4 bytes) or 64-bit (8 bytes).

The alignment settings should always be left at 0 unless corruption is done on an experimental target or file, or if the game that is being corrupted mispositions its data.
