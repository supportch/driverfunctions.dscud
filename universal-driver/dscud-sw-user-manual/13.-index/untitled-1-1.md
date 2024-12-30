---
description: This product is supported for DSCUD 8.0 and above.
---

# Opal-MM

### Board Initialization

To use the Opal-MM board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_OPMM. This is shown in the example below.

```c
dscInitBoard( DSC_OPMM , &dsccb, &board );
```

### Digital I/O

|                   |                                                                                                                                                                                                                 |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Interrupts        | Not supported on this board.                                                                                                                                                                                    |
| Max Input Ports:  | 8 lines (1 byte or 8 bits), optoisolated, inverting logic (high input = 0, low input = 1)                                                                                                                       |
| Max Output Ports: | 8 lines (1 byte or 8 bits), type SPDT (form C) relays A 1 in each bit turns that relay on, and a 0 turns it off. All relays power up in the off (0) position. The output ports do not have readback capability. |

The inputs and outputs are fixed direction and do not need configuration prior to use.

### Opal-MM Universal Driver Functions

* [dscDIOClearBit() ](../14.-universal-driver-apis/dscdioclearbit.md)
* [dscDIOInputBit()](../14.-universal-driver-apis/dscdioinputbit.md)&#x20;
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOOutputBit() ](../14.-universal-driver-apis/dscdiooutputbit.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOSetBit()](../14.-universal-driver-apis/dscdiosetbit.md)
* dscGetRelay()
* dscGetRelayMulti()
* dscSetRelay()
* dscSetRelayMulti()
