# MelonDS-Specific Lists

{% hint style="danger" %}
The Nintendo DS's architechture does not support IEEE754 Floats and isn't compatible with the built-in Vector Engine lists. Special lists with the NDS prefix are bundled with MelonDS-Vanguard.
{% endhint %}

### System-specific Vector Engine Lists that come with Dolphin-Vanguard

* **NDS\_Extended**: -65536.00 to +65536.00 in low res, including tiny decimals
* **NDS\_NOP\_ARM**: Value for No Operation instruction (Standard instruction set)
* **NDS\_NOP\_THUMB2**: Value for No Operation instruction (Thumb 2 instruction set)
* **NDS\_NOP\_THUMB4**: Value for No Operation instruction (Thumb 4 instruction set)
* **NDS\_One**: The numbers +1.00 and -1.00
* **NDS\_Two**: The number +2.00
* **NDS\_Whole**: -65536.00 to +65536.00 in low res, integral numbers

_Also check this link for the default lists that come with the Vector Engine_

{% content-ref url="../../rtcv/rtc/classic-vector-lists.md" %}
[classic-vector-lists.md](../../rtcv/rtc/classic-vector-lists.md)
{% endcontent-ref %}

### Usage

Since the Nintendo DS isn't compliant with IEEE754, the default lists of the Vector Engine cannot be used. The Extended,One,Two,Whole lists should behave like their counterparts. The NOP Lists can be used as Value lists to cause game code to break.
