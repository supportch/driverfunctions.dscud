# Helix

This product is supported for DSCUD 8.0 and above. For DSCUD 7.0 documentation, please refer [HELIX SBC Universal Driver Software User Manual A0.pdf](http://diamondsystems.com/files/binaries/HELIX%20SBC%20Universal%20Driver%20Software%20User%20Manual%20A0.pdf)

### Overview

Helix SBCs use the Vortex86DX3 SoC from DMP Electronics. It is a 32-bit x86 architecture dual-core 1GHz microprocessor designed for ultra-low power consumption, combining both the North and South bridges with a rich set of integrated features including a 32KB write through 8-way L1 cache, 512KB write through/write back 4- way L2 cache, PCIe bus at 2.5 GHz, DDR3 controller, ISA, I2C, SPI, IPC (includes Internal Peripheral Controllers with DMA and interrupt timer/counter), Fast Ethernet, FIFO UART, USB2.0 Host, and an IDE/SATA controller. The SBC supports up to 2GB of DDR3 memory soldered on-board.

The SBC provides four serial ports: two with fixed RS-232 capability using SP211EHEA-L, and a second two having RS-232/422/485 capability using a SP336. The built-in UARTs from the VortexDX3 are used. In RS-232 mode, only the signals TX, RX, RTS, and CTS are provided. Protocol selection for serial ports 3-4 is controlled using GPIO pins from the SoC and is configurable via BIOS configuration screens as well as via application software. Jumpers are used to enable termination resistors (121 Ohm) for RS-422 and RS-485 protocols. Console redirection, using a serial port

### Board Initialization

To use the Helix board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_HELIX. This is shown in the example below.

```c
dscInitBoard(DSC_HELIX, &dsccb, &board );
```

### Analog Input

|                                             |                                                                            |
| ------------------------------------------- | -------------------------------------------------------------------------- |
| Max Input Channels:                         | 16 (single-ended) or 8 (differential)                                      |
| A/D Resolution:                             | 16 bits (1/65536 of full-scale)                                            |
| Data range:                                 | -32768 to +32767 for all voltage ranges                                    |
| Input Ranges (Bipolar):                     | ±10V, ±5V                                                                  |
| Input Ranges (Unipolar):                    | 0-10V, 0-5V.                                                               |
| Supported Conversion Triggers:              | Software, External digital signal, programmable clock.                     |
| Maximum Conversion Rate (Software Command): | approx. 100,000 samples per second, depending on code and operating system |
| FIFO:                                       | 2048 samples with Programmable interrupt threshold                         |

### Analog Output

|                         |                                   |
| ----------------------- | --------------------------------- |
| Max Output Channels:    | 4                                 |
| D/A Resolution:         | 16 bits (1/65536 of full scale)   |
| Data range:             | 0 to 65535 for all voltage ranges |
| Bipolar Output Ranges:  | ±10V, ±5V.                        |
| Unipolar Output Ranges: | 0-5V, 0-2.5V.                     |

### Digital I/O

|            |                                                                                                                                                                                                                                                                                                                                                        |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Max Ports: | 3, bi-directional, 27 lines organized as 2 8-bit ports and 11 1-bit ports on Prometheus require direction to be set with DscDIOSetConfig() before use. All DIO lines power-up in input mode and have readback capability. All DIO lines have User-selectable 10K pull resistors that can be configured for all pull-up or all pull-down with a jumper. |

### Helix Universal Driver Functions

* [dscADIntCancel()](../14.-universal-driver-apis/dscadintcancel.md)&#x20;
* [dscADIntStatus() ](../14.-universal-driver-apis/dscadintstatus.md)
* [dscADSample() ](../14.-universal-driver-apis/dscadsample.md)
* [dscADSampleInt()](../14.-universal-driver-apis/dscadsampleint.md)&#x20;
* [dscADScan() ](../14.-universal-driver-apis/dscadscan.md)
* [dscADSetSettings() ](../14.-universal-driver-apis/dscadsetsettings.md)
* [dscADSetTiming() ](../14.-universal-driver-apis/dscadsettiming.md)
* [dscCancelOpType() ](../14.-universal-driver-apis/dsccanceloptype.md)
* [dscCounterConfig() ](../14.-universal-driver-apis/dsccounterconfig.md)
* [dscCounterDirectSet() ](../14.-universal-driver-apis/dsccounterdirectset.md)
* [dscCounterFunction() ](../14.-universal-driver-apis/dsccounterfunction.md)
* [dscCounterRate()](../14.-universal-driver-apis/dsccounterrate.md)&#x20;
* [dscCounterRead() ](../14.-universal-driver-apis/dsccounterread.md)
* [dscCounterReset() ](../14.-universal-driver-apis/dsccounterreset.md)
* [dscDAConvert() ](../14.-universal-driver-apis/dscdaconvert.md)
* [dscDAConvertScan()](../14.-universal-driver-apis/dscdaconvertscan.md)&#x20;
* [dscDASetSettings()](../14.-universal-driver-apis/dscdasetsettings.md)&#x20;
* [dscDIOInputBit() ](../14.-universal-driver-apis/dscdioinputbit.md)
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOIntCancel()](../14.-universal-driver-apis/dscadintcancel.md)&#x20;
* [dscDIOOutputBit() ](../14.-universal-driver-apis/dscdiooutputbit.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOOutputInt() ](../14.-universal-driver-apis/dscdiooutputint.md)
* [dscDIOSetConfig() ](../14.-universal-driver-apis/dscdiosetconfig.md)
* [dscLEDTest() ](../14.-universal-driver-apis/dscledtest.md)
* [dscPauseOp() ](../14.-universal-driver-apis/dscpauseop.md)
* [dscPWMClear() ](../14.-universal-driver-apis/dscpwmclear.md)
* [dscPWMStart() ](../14.-universal-driver-apis/dscpwmstart.md)
* [dscResumeOp() ](../14.-universal-driver-apis/dscresumeop.md)
* [dscUserInt()](../14.-universal-driver-apis/dscuserint.md)&#x20;
* [dscUserIntRun() ](../14.-universal-driver-apis/dscuserintrun.md)
* [dscWGBufferLoad()](../14.-universal-driver-apis/dscwgbufferload.md)&#x20;
* [dscWGCommand() ](../14.-universal-driver-apis/dscwgcommand.md)
* [dscWGConfigSet()](../14.-universal-driver-apis/dscwgconfigset.md)
