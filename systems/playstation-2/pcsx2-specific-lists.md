# PCSX2-specific Lists

### System-specific Vector Engine Lists that come with PCSX2-Vanguard

* **PCSX2 BALL**: (Branch ALL) Contains all the Branch lists
* **PCSX2 BEQ**: (Branch Equal) Multiple possible values for code branching with IF EQUAL operation
* **PCSX2 BG**: (Branch Greater) Multiple possible values for code branching with IF GREATER operation
* **PCSX2 BL**: (Branch Less) Multiple possible values for code branching with IF LESS operation
* **PCSX2 BNE**: (Branch Not Equal) Multiple possible values for code branching with IF NOT EQUAL operation
* **PCSX2 NOP**: (No Operation) Contains the value 0x00000000 which is used to cancel an operation



_Also check this link for the default lists that come with the Vector Engine_

{% content-ref url="../../rtcv/rtc/classic-vector-lists.md" %}
[classic-vector-lists.md](../../rtcv/rtc/classic-vector-lists.md)
{% endcontent-ref %}

### Usage

These are lists that contain many variations of values used by program code. Corrupting using these value lists dramatically increases the chances of hitting game code.

For general purposes, a recommended usage is any Branch lists as Limiter and the NOP list as a Value. Play around with the Branch lists. You can also swap the Limiter and Value lists for different results.

### Limitations of the lists

The PCSX2 lists were added in 5.0.4. The Branch lists currently only a limited amount of possible values (-200 to +200 generally).

### Extra documentation on PS2 Architechture

[http://www.cs.tau.ac.il/\~afek/MipsInstructionSetReference.pdf](http://www.cs.tau.ac.il/\~afek/MipsInstructionSetReference.pdf) : General documentation on the Mips Instruction set\
[http://www-soc.lip6.fr/\~marchett/Archi\_Memento\_MIPS-nup.pdf](http://www-soc.lip6.fr/\~marchett/Archi\_Memento\_MIPS-nup.pdf) : Arithmetic-specific documentation on the MIPS Instruction set (French)
