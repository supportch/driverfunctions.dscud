---
description: This product is supported for DSCUD 8.0 and above.
---

# Onyx-MM

### Board Initialization

To use the Onyx-MM board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_OMM. This is shown in the example below.

```c
dscInitBoard( DSC_OMM , &dsccb, &board );
```

### Digital I/O

|                 |                                                                                                                                                                                                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ports:          | 6 8-bit bidirectional ports (2 82C55 chips) Digital I/O ports on Onyx-MM require direction to be set with dscDIOSetConfig before use. One configuration byte is required for each 82C55 chip. All DIO lines power-up in input mode and have readback capability. All DIO lines have 10K Ohm pull-up resistors. |
| Interrupts:     | 3 interrupts with programmable sources and jumper-configured IRQ levels                                                                                                                                                                                                                                        |
| Counter/Timers: | 3 16-bit counter/timers with programmable sources and cascading                                                                                                                                                                                                                                                |

Refer to the Onyx-MM user manual for detailed information on the counter and interrupt circuit features and configuration. Also refer to the user interrupt function descriptions in this manual for information on how to configure the counters and interrupts for your application.

### Onyx-MM Universal Driver Functions

* [dscClearUserInterruptFunction() ](../14.-universal-driver-apis/dscclearuserinterruptfunction.md)
* [dscCounterDirectSet()](../14.-universal-driver-apis/dsccounterdirectset.md)&#x20;
* [dscCounterRead() ](../14.-universal-driver-apis/dsccounterread.md)
* [dscCounterSetRate() ](../14.-universal-driver-apis/dsccountersetrate.md)
* [dscCounterSetRateSingle() ](../14.-universal-driver-apis/dsccountersetratesingle.md)
* [dscDIOClearBit() ](../14.-universal-driver-apis/dscdioclearbit.md)
* [dscDIOInputBit() ](../14.-universal-driver-apis/dscdioinputbit.md)
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOOutputBit() ](../14.-universal-driver-apis/dscdiooutputbit.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOSetBit() ](../14.-universal-driver-apis/dscdiosetbit.md)
* [dscDIOSetConfig() ](../14.-universal-driver-apis/dscdiosetconfig.md)
* [dscSetUserInterruptFunction() ](../14.-universal-driver-apis/dscsetuserinterruptfunction.md)
* [dscUserInt()](../14.-universal-driver-apis/dscuserint.md)
