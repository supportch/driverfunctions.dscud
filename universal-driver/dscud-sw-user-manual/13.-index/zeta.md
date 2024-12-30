---
description: This product is supported for DSCUD 8.0 and above.
---

# Zeta

### Overview

The Zeta COM Express SBC family of ultra-small embedded computer boards combines a COM Express Mini CPU module mounted on a same-size carrier board to create a complete embedded PC. Zeta integrates onboard memory, one PCIe/MiniCard socket, dual Gigabit Ethernet, and optional data acquisition circuit with analog and digital I/O.

The SBC provides an optional data acquisition circuit containing analog input, analog output, and additional digital I/O features. This circuit is controlled by an FPGA interfaced to the processor via LPC.

### Board Initialization

To use the Zeta board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_ZETA. This is shown in the example below.

The base address should be 0x200 and the default IRQ to use is IRQ 5.

```c
dscInitBoard(DSC_ZETA, &dsccb, &board );
```

### Analog Input

|                                             |                                                                             |
| ------------------------------------------- | --------------------------------------------------------------------------- |
| Max Input Channels:                         | 16 (single-ended) or 8 (differential)                                       |
| A/D Resolution:                             | 16 bits (1/65536 of full-scale)                                             |
| Data range:                                 | -32768 to +32767 for all voltrage ranges.                                   |
| Input Ranges (Bipolar):                     | ±10V, ±5V                                                                   |
| Input Ranges (Unipolar):                    | 0-10V, 0-5V.                                                                |
| Supported Conversion Triggers:              | Software, External digital signal, programmable clock.                      |
| Maximum Conversion Rate (Software Command): | approx. 100,000 samples per second, depending on code and operating system. |
| FIFO:                                       | 2048 samples with Programmable interrupt threshold.                         |

### Analog Output

|                         |                                   |
| ----------------------- | --------------------------------- |
| Max Output Channels:    | 4                                 |
| D/A Resolution:         | 16 bits (1/65536 of full scale)   |
| Data range:             | 0 to 65535 for all voltage ranges |
| Bipolar Output Ranges:  | ±10V, ±5V.                        |
| Unipolar Output Ranges: | 0-10V, 0-5V                       |

### Digital I/O

|            |                                                                                                                                                                                                                                                                                                                                                     |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Max Ports: | 3, bi-directional, 27 lines organized as 2 8-bit ports and 11 1-bit portson Prometheus require direction to be set with DscDIOSetConfig before use. All DIO lines power-up in input mode and have readback capability. All DIO lines have User-selectable 10K pull resistors that can be configured for all pull-up or all pull-down with a jumper. |

### Zeta Universal Driver Functions

* [dscADIntCancel() ](../14.-universal-driver-apis/dscadintcancel.md)
* [dscADIntStatus() ](../14.-universal-driver-apis/dscadintstatus.md)
* [dscADSample() ](../14.-universal-driver-apis/dscadsample.md)
* [dscADSampleInt() ](../14.-universal-driver-apis/dscadsampleint.md)
* [dscADScan() ](../14.-universal-driver-apis/dscadscan.md)
* [dscADSetSettings() ](../14.-universal-driver-apis/dscadsetsettings.md)
* [dscADSetTiming() ](../14.-universal-driver-apis/dscadsettiming.md)
* [dscCancelOpType() ](../14.-universal-driver-apis/dsccanceloptype.md)
* [dscCounterConfig() ](../14.-universal-driver-apis/dsccounterconfig.md)
* [dscCounterDirectSet() ](../14.-universal-driver-apis/dsccounterdirectset.md)
* [dscCounterRate() ](../14.-universal-driver-apis/dsccounterrate.md)
* [dscCounterRead() ](../14.-universal-driver-apis/dsccounterread.md)
* [dscCounterReset() ](../14.-universal-driver-apis/dsccounterreset.md)
* [dscDAConvert() ](../14.-universal-driver-apis/dscdaconvert.md)
* [dscDAConvertScan() ](../14.-universal-driver-apis/dscdaconvertscan.md)
* [dscDASetSettings() ](../14.-universal-driver-apis/dscdasetsettings.md)
* [dscDIOInputBit() ](../14.-universal-driver-apis/dscdioinputbit.md)
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOIntCancel() ](../14.-universal-driver-apis/dscdiointcancel.md)
* [dscDIOOutputBit() ](../14.-universal-driver-apis/dscdiooutputbit.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOOutputInt() ](../14.-universal-driver-apis/dscdiooutputint.md)
* [dscDIOSetConfig() ](../14.-universal-driver-apis/dscdiosetconfig.md)
* [dscLEDTest() ](../14.-universal-driver-apis/dscledtest.md)
* [dscPauseOp() ](../14.-universal-driver-apis/dscpauseop.md)
* [dscPWMClear() ](../14.-universal-driver-apis/dscpwmclear.md)
* [dscPWMStart() ](../14.-universal-driver-apis/dscpwmstart.md)
* [dscResumeOp() ](../14.-universal-driver-apis/dscresumeop.md)
* [dscUserInt() ](../14.-universal-driver-apis/dscuserint.md)
* [dscUserIntRun() ](../14.-universal-driver-apis/dscuserintrun.md)
* [dscWGBufferLoad() ](../14.-universal-driver-apis/dscwgbufferload.md)
* [dscWGCommand() ](../14.-universal-driver-apis/dscwgcommand.md)
* [dscWGConfigSet()](../14.-universal-driver-apis/dscwgconfigset.md)
