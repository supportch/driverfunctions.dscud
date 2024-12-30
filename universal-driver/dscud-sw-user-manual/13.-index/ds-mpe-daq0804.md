# DS-MPE-DAQ0804

This product is supported for DSCUD 8.0 and above. For DSCUD 7.0 documentation, please refer [DS-MPE-DAQ0804 Universal Driver Software User Manual A.0.pdf](http://diamondsystems.com/files/binaries/DS-MPE-DAQ0804%20Universal%20Driver%20User%20Manual.pdf)

### Overview

DS-MPE-DAQ0804 is a rugged data acquisition PCIe MiniCard module consisting of both analog and configurable digital I/O. The module is ideal for add-on data acquisition I/O expansion in embedded and OEM applications. The PCIe MiniCard offers 8 single ended or four differential 16-bit analog inputs with an aggregate sample rate of 100KHz maximum, 2048 sample A/D FIFO, four 16-bit analog outputs, and 14 digital I/O lines. The buffered digital I/O lines can be optionally configured as either pulse width modulators or counter/timers.

Diamond’s Universal Driver 8.1.0 software provides driver support for all functions. The DS-MPE-DAQ0804 product comes with the PCIe MiniCard data acquisition I/O module, the CK-DAQ0804 cable kit, and a hardware kit with jumpers and screws.

### Board Initialization

To use the DS-MPE-DAQ0804 board in an appllication using the UD, the dscPCIInitBoard function should use the board macro DSC\_MPEDAQ0804. This is shown in the example below.

```c
dscPCIInitBoard(DSC_MPEDAQ0804 , &dsccb, &board );
```

### A/D Features

|                                                                                     |
| ----------------------------------------------------------------------------------- |
| 16 analog voltage inputs                                                            |
| 16-bit resolution (1 part in 65536)                                                 |
| Programmable input ranges: 0-5V, 0-10V, +/-5v, +/-10V                               |
| Single-ended and differential input configuration options                           |
| Precision, low-drift 2.5V reference voltage                                         |
| 100KHz maximum total A/D sample rate (all active channels combined)                 |
| Integrated 2048-sample FIFO and interrupt service for efficient high-speed sampling |

### D/A Features

|                                                                                                  |
| ------------------------------------------------------------------------------------------------ |
| 4 analog voltage outputs                                                                         |
| 16-bit resolution (1 part in 65536)                                                              |
| Single-channel and multi-channel simultaneous update modes                                       |
| Programmable output range: 0-5V, 0-2.5V                                                          |
| 30KHz update rate capability                                                                     |
| Waveform generator on 1 to 4 outputs with user-defined waveforms and 2048-sample waveform buffer |

### Digital I/O features

|                                                                                               |
| --------------------------------------------------------------------------------------------- |
| 21 digital I/O lines                                                                          |
| 3.3V logic levels                                                                             |
| User-configurable 10K pull-up / pull-down resistors                                           |
| Individually programmable direction for each line                                             |
| 8-bit programmable edge detection circuit                                                     |
| Buffers for protection and higher current drive                                               |
| 8 32-bit counter/timers with up counting, down counting, pulse output, and interrupt features |
| 4 24-bit pulse-width modulators with programmable duty cycle and output polarity              |
| Interrupt support for A/D, digital I/O, and counter/timer circuits                            |

### DS-MPE-DAQ0804 Universal Driver Functions

* [dscADIntCancel() ](../14.-universal-driver-apis/dscadintcancel.md)
* [dscADIntStatus() ](../14.-universal-driver-apis/dscadintstatus.md)
* [dscADSample() ](../14.-universal-driver-apis/dscadsample.md)
* [dscADSampleInt()](../14.-universal-driver-apis/dscadsampleint.md)&#x20;
* [dscADScan() ](../14.-universal-driver-apis/dscadscan.md)
* [dscADSetSettings()](../14.-universal-driver-apis/dscadsetsettings.md)&#x20;
* [dscADSetTiming() ](../14.-universal-driver-apis/dscadsettiming.md)
* [dscCancelOp() ](../14.-universal-driver-apis/dsccancelop.md)
* [dscCounterConfig() ](../14.-universal-driver-apis/dsccounterconfig.md)
* [dscCounterRate() ](../14.-universal-driver-apis/dsccounterrate.md)
* [dscCounterRead() ](../14.-universal-driver-apis/dsccounterread.md)
* [dscCounterReset() ](../14.-universal-driver-apis/dsccounterreset.md)
* [dscDAConvert() ](../14.-universal-driver-apis/dscdaconvert.md)
* [dscDAConvertScan() ](../14.-universal-driver-apis/dscdaconvertscan.md)
* [dscDASetSettings() ](../14.-universal-driver-apis/dscdasetsettings.md)
* [dscDIOInputBit()](../14.-universal-driver-apis/dscdioinputbit.md)&#x20;
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOOutputBit() ](../14.-universal-driver-apis/dscdiooutputbit.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOSetConfig()](../14.-universal-driver-apis/dscdiosetconfig.md)
* [dscLEDTest()](../14.-universal-driver-apis/dscledtest.md)&#x20;
* [dscPauseOp() ](../14.-universal-driver-apis/dscpauseop.md)
* [dscPWMClear() ](../14.-universal-driver-apis/dscpwmclear.md)
* [dscPWMStart()](../14.-universal-driver-apis/dscpwmstart.md)&#x20;
* [dscResumeOp() ](../14.-universal-driver-apis/dscresumeop.md)
* [dscUserInt()](../14.-universal-driver-apis/dscuserint.md)&#x20;
* [dscUserIntRun() ](../14.-universal-driver-apis/dscuserintrun.md)
* [dscWGBufferLoad() ](../14.-universal-driver-apis/dscwgbufferload.md)
* [dscWGCommand() ](../14.-universal-driver-apis/dscwgcommand.md)
* [dscWGConfigSet()](../14.-universal-driver-apis/dscwgconfigset.md)
