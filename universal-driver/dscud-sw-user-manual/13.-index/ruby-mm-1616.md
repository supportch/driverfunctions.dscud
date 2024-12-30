# Ruby-MM-1616

This product is supported for DSCUD 8.0 and above. For DSCUD 7.0 documentation, please refer [RMM-1616\_Universal\_Driver\_Software\_ User\_Manual A.0.pdf](http://diamondsystems.com/files/binaries/RMM-1616_Universal%20Manual%20A.0.pdf)

### Overview

The RMM-1616A/AP is a family of PC/104 and PC/104-Plus I/O modules featuring 4, 8 or 16 16-bit analog voltage and current outputs, and 48 digital I/O lines. A 50-pin connector provides access to the 16 analog outputs, and another 50-pin connector provides access to the 48 digital I/O lines. The board operates over the extended temperature range of -40oC to +85oC

### Board Initialization

To use the Ruby-MM-1616 board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_RMM1616. This is shown in the example below.

```c
dscInitBoard(DSC_RMM1616, &dsccb, &board );
```

### Analog Input

Not supported by this board.

### Analog Output

|                           |                                                      |
| ------------------------- | ---------------------------------------------------- |
| Max Output Channels:      | 16                                                   |
| D/A Resolution:           | 16 bits (1/65536 of full-scale)                      |
| Data Range:               | 0 to 65535                                           |
| Output Ranges (Bipolar):  | ±10V, ±5V (per each bank of 8 channels via jumper)   |
| Output Ranges (Unipolar): | 0-10V, 0-5V (per each bank of 8 channels via jumper) |

### Digital I/O

|            |                                                                                                                                                                                                                                                                                            |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Max Ports: | 6 bi-directional, programmable in 8-bit groups, TTL-compatible Digital I/O ports on Ruby-MM-1616 require direction to be set with DscDIOSetConfig() before use. All DIO lines power-up in input mode and have readback capability. All DIO lines have User configurable pull-up resistors. |

### Ruby-MM-1616 Universal Driver Functions

* [dscCancelOpType() ](../14.-universal-driver-apis/dsccanceloptype.md)
* [dscCounterConfig() ](../14.-universal-driver-apis/dsccounterconfig.md)
* [dscCounterFunction() ](../14.-universal-driver-apis/dsccounterfunction.md)
* [dscCounterRate() ](../14.-universal-driver-apis/dsccounterrate.md)
* [dscCounterRead() ](../14.-universal-driver-apis/dsccounterread.md)
* [dscDAConvert() ](../14.-universal-driver-apis/dscdaconvert.md)
* [dscDAConvertScan() ](../14.-universal-driver-apis/dscdaconvertscan.md)
* [dscDASetSettings() ](../14.-universal-driver-apis/dscdasetsettings.md)
* [dscDASetSim()](../14.-universal-driver-apis/dscdasetsim.md)&#x20;
* [dscDIOInputBit()](../14.-universal-driver-apis/dscdioinputbit.md)&#x20;
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOOutputBit() ](../14.-universal-driver-apis/dscdiooutputbit.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOSetConfig() ](../14.-universal-driver-apis/dscdiosetconfig.md)
* [dscLEDTest() ](../14.-universal-driver-apis/dscledtest.md)
* [dscPWMClear() ](../14.-universal-driver-apis/dscpwmclear.md)
* [dscPWMStart() ](../14.-universal-driver-apis/dscpwmstart.md)
* [dscSetPage() ](../14.-universal-driver-apis/dscsetpage.md)
* [dscUserInt() ](../14.-universal-driver-apis/dscuserint.md)
* [dscWGBufferLoad() ](../14.-universal-driver-apis/dscwgbufferload.md)
* [dscWGCommand() ](../14.-universal-driver-apis/dscwgcommand.md)
* [dscWGConfigSet()](../14.-universal-driver-apis/dscwgconfigset.md)
