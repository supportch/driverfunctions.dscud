# Diamond-MM-16RP-AT

## Overview

Currently C# APIs supports, only for windows 10 64 bit OS. DMM-16RP-AT is a of PC/104 and PC/104-Plus I/O modules featuring analog and digital I/O modules. The module is ideal for add-on data acquisition I/O expansion in embedded and OEM applications. It offers 16 single ended or 8 differential 16-bit analog inputs with an aggregate sample rate of 100 KHz maximum, 512 sample A/D FIFO, four 12-bit analog outputs, and 16 digital I/O lines. The buffered digital I/O lines can be optionally configured as either pulse width modulators or counter/timers.

## Board Initialization

To use the Diamond-MM-16RP-AT board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_DMM16RPAT. This is shown in the example below.

```csharp
dscInitBoard(DSCUD_class.DSC_DMM16RPAT, ref dsccb, ref (DSCUD_class.dscb);
```

## Analog Input

|                                             |                                                                            |
| ------------------------------------------- | -------------------------------------------------------------------------- |
| Max Input Channels:                         | 16 (single-ended) or 8 (differential)                                      |
| A/D Resolution:                             | 16 bits (1/65536 of full-scale)                                            |
| Data range:                                 | -32768 to +32767 for all voltrage ranges                                   |
| Input Ranges (Bipolar):                     | ±10V, ±5V, ±2.5V, ±1.25V                                                   |
| Input Ranges (Unipolar):                    | 0-10V, 0-5V,0-2.5V                                                         |
| Supported Conversion Triggers:              | Software, External digital signal, programmable clock.                     |
| Maximum Conversion Rate (Software Command): | approx. 100,000 samples per second, depending on code and operating system |
| FIFO:                                       | 512 samples with Programmable interrupt threshold                          |

## Analog Output

|                         |                                  |
| ----------------------- | -------------------------------- |
| Max Output Channels:    | 4                                |
| D/A Resolution:         | 12 bits (1/4096 of full scale)   |
| Data range:             | 0 to 4095 for all voltage ranges |
| Bipolar Output Ranges:  | ±5V                              |
| Unipolar Output Ranges: | 0-5V, 0 – (user-programmable)    |

## Digital I/O

|            |                                                                                                                                                                                                                                                                                                  |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Max Ports: | 2, two 8-bit ports and Prometheus require direction to be set with DscDIOSetConfig() before use. All DIO lines power-up in input mode and have readback capability. All DIO lines have User-selectable 10K pull resistors that can be configured for all pull-up or all pull-down with a jumper. |

## Diamond-MM-16-AT Universal Driver Functions

* dscADAutoCal()&#x20;
* dscADCalVerify()
* dscADSample()&#x20;
* dscADScan()&#x20;
* dscADSetChannel()
* dscADSetSettings()&#x20;
* dscCounterRead()
* dscCounterSetRateSingle()&#x20;
* dscDAAutoCal()&#x20;
* dscDACalVerify()&#x20;
* dscDAConvert()
* dscDAConvertScan()&#x20;
* dscDIOInputBit()&#x20;
* dscDIOInputByte()&#x20;
* dscDIOOutputBit()&#x20;
* dscDIOOutputByte()&#x20;
* dscDIOSetConfig()
* dscGetEEPROM()
* dscGetReferenceVoltages() &#x20;
* dscLEDTest()&#x20;
* dscSetCalMux()&#x20;
* dscSetReferenceVoltages()
