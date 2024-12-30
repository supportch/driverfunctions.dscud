---
description: This product is supported for DSCUD 8.0 and above.
---

# Athena-IV

## Overview

The Athena IV is a COM carrier board that provides physical conformance to the Athena II and III SBCs to the greatest extent possible. It is intended to be used as a replacement product for customers of Athena II and III. Instead of a single board computer design, Athena IV is a COM carrier that uses COM Express Mini type 10 modules to provide the CPU functionality. The board maintains the PC/104 stack through ISA bus that is used on Athena II / III. Athena IV is available in two configurations, with data acquisition. The data acquisition circuit is identical to the one on Athena II. The Athena IV SBC is based on Intel "E3845" series processors.

The SBC provides an optional data acquisition circuit containing analog input, analog output, and digital I/O features. This circuit is controlled by an FPGA interfaced to the processor via LPC.

### Board Initialization

To use the Athena IV board in an application using the UD, the dscInitBoard function should use the board macro DSC\_ATHENAIV. This is shown in the example below...&#x20;

The base address should be 0x280 and the default IRQ to use is IRQ 5.&#x20;

```c
dscInitBoard(DSC_ATHENAIV, &dsccb, &board );
```

### Analog Input

|                                                     |                                                                            |
| --------------------------------------------------- | -------------------------------------------------------------------------- |
| Max Input Channels:                                 | 16 (single-ended) or 8 (differential)                                      |
| A/D Resolution:                                     | 16 bits (1/65536 of full-scale)                                            |
| Data range:                                         | -32768 to +32767 for all voltage ranges                                    |
| Input Ranges (Bipolar):                             | ±10V, ±5V, ±2.5V, or ±1.25V                                                |
| Input Ranges (Unipolar):                            | 0-10V, 0-5V, or 0-2.5V                                                     |
| Supported Conversion Triggers:                      | Software, External signal                                                  |
| Maximum Conversion Rate (Software Command):         | approx. 250,000 samples per second, depending on code and operating system |
| Maximum Conversion Rate (Interrupt Routine w/FIFO): | 100,000 samples per second                                                 |
| FIFO:                                               |  2048 samples with Programmable interrupt threshold                        |

### Analog Output

|                          |                                  |
| ------------------------ | -------------------------------- |
| Max Output Channels:     | 4                                |
| D/A Resolution:          | 12 bits (1/4096 of full scale)   |
| Data range:              | 0 to 4096 for all voltage ranges |
| Bipolar Output Ranges:   | ±10V                             |
| Uni-polar Output Ranges: | 0-10V                            |

### Digital I/O

|            |                                                                                                                                                                                                                                                                                                                                                                                         |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Max Ports: | <p>24 digital I/O in 3 8-bit ports with programmable direction and buffered outputs on Prometheus require direction to be set with DscDIOSetConfig() before use. </p><p>All DIO lines power-up in input mode and have read-back capability. </p><p>All DIO lines have r external configurable pull resistors that can be configured for all pull-up or all pull-down with a jumper.</p> |

### Athena-IV Universal Driver Functions <a href="#aries-universal-driver-functions" id="aries-universal-driver-functions"></a>

* ​[dscADAutoCal()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscadautocal) ​
* ​[dscADCalVerify()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscadcalverify)
* ​[dscGetStatus()](../14.-universal-driver-apis/dscgetstatus.md) ​
* ​[dscADSample()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscadsample) ​
* ​[dscADSampleInt ()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscadsampleint) ​
* ​[dscADScan()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscadscan) ​
* ​[dscADScanInt () ​](../14.-universal-driver-apis/dscadscanint.md)
* ​[dscADSetSettings()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscadsetsettings)
* ​[dscCancelOp()](../14.-universal-driver-apis/dsccancelop.md)
* [dscDAAutoCal()](../14.-universal-driver-apis/dscdaautocal.md)
* [dscDACalVerify()](../14.-universal-driver-apis/dscdacalverify.md)
* [dscDAConvert()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscdaconvert)
* ​[dscDAConvertScan()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscdaconvertscan)
* ​[dscDASetSettings()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscdasetsettings)
* ​[dscDIOInputBit()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscdioinputbit)
* ​[dscDIOInputByte()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscdioinputbyte) ​
* ​[dscDIOOutputBit()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscdiooutputbit) ​
* ​[dscDIOOutputByte()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscdiooutputbyte)
* ​[dscDIOSetConfig()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscdiosetconfig)
* ​[dscLEDTest()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscledtest) ​
* [dscGetReferenceVoltages()](../14.-universal-driver-apis/dscgetreferencevoltages.md)
* [dscSetCalMux()](../14.-universal-driver-apis/dscsetcalmux.md)
* [dscADSetChannel()](../14.-universal-driver-apis/dscadsetchannel.md)
* [dscSetReferenceVoltages()](../14.-universal-driver-apis/dscsetreferencevoltages.md)
* [dscSetUserInterruptFunction()](../14.-universal-driver-apis/dscsetuserinterruptfunction.md)
* [dscClearUserInterruptFunction()](../14.-universal-driver-apis/dscclearuserinterruptfunction.md)
* ​[dscUserInt()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscuserint)
* ​[dscWatchdogDisable()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscwatchdogdisable)
* ​[dscWatchdogEnable()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscwatchdogenable)
* ​[dscWatchdogTrigger()](https://diamondsystems.gitbook.io/user-manuals/universal-driver-software-user-manual/14.-universal-driver-apis/dscwatchdogtrigger)​

