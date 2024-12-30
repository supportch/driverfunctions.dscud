---
description: This product is supported for DSCUD 8.0 and above.
---

# Diamond-MM-16-AT

### Board Initialization

To use the DMM-16-AT board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_DMM16. This is shown in the example below.

```c
dscInitBoard( DSC_DMM16, &dsccb, &board );
```

### Analog Input

|                                                     |                                                  |
| --------------------------------------------------- | ------------------------------------------------ |
| Max Input Channels:                                 | 16 (single-ended) or 8 (differential)            |
| A/D Resolution:                                     | 16 bits (1/65536 of full-scale)                  |
| Data range:                                         | -32768 to +32767 for all voltage ranges          |
| Input Ranges (Bipolar):                             | ±10V, ±5V, ±2.5V, or ±1.25V                      |
| Input Ranges (Unipolar):                            | 0-10V, 0-5V, or 0-2.5V                           |
| Supported Conversion Triggers:                      | Software, Internal Clock, or External TTL Signal |
| Maximum Conversion Rate (Software Command):         | 2,000 (approx.) samples per second               |
| Maximum Conversion Rate (Interrupt Routine w/FIFO): | 100,000 samples per second                       |
| FIFO:                                               | 512 samples with fixed threshold of 256          |

This board supports the following programmable input ranges and resolutions:

{% tabs %}
{% tab title="A/D Ranges" %}
| Code | Range | ADBU | G1 | G0 | Input Range     | Resolution (1 LSB) |
| ---- | ----- | ---- | -- | -- | --------------- | ------------------ |
| 0    | 0     | 0    | 0  | 0  | ±5V             | 153μV              |
| 1    | 0     | 0    | 0  | 1  | ±2.5V           | 76μV               |
| 2    | 0     | 0    | 1  | 0  | ±1.25V          | 38μV               |
| 3    | 0     | 0    | 1  | 1  | Invalid Setting | -                  |
| 4    | 0     | 1    | 0  | 0  | Invalid Setting | -                  |
| 5    | 0     | 1    | 0  | 1  | Invalid Setting | -                  |
| 6    | 0     | 1    | 1  | 0  | Invalid Setting | -                  |
| 7    | 0     | 1    | 1  | 1  | Invalid Setting | -                  |
| 8    | 1     | 0    | 0  | 0  | ±10V            | 305μV              |
| 9    | 1     | 0    | 0  | 1  | ±5V             | 153μV              |
| 10   | 1     | 0    | 1  | 0  | ±2.5V           | 76μV               |
| 11   | 1     | 0    | 1  | 1  | ±1.25V          | 38μV               |
| 12   | 1     | 1    | 0  | 0  | 0 - 10V         | 153μV              |
| 13   | 1     | 1    | 0  | 1  | 0 - 5V          | 76μV               |
| 14   | 1     | 1    | 1  | 0  | 0 - 2.5V        | 38μV               |
| 15   | 1     | 1    | 1  | 1  | Invalid Setting | -                  |
{% endtab %}
{% endtabs %}

NOTE: The A/D modes for codes 3 through 7 and 15 are invalid, and the settings for codes 9 through 11 are identical to codes 0 through 2.

### Analog Output (model DMM-16-AT only)

|                                         |                                  |
| --------------------------------------- | -------------------------------- |
| Max Output Channels:                    | 4                                |
| D/A Resolution:                         | 12 bits (1/4096 of full-scale)   |
| Data range:                             | 0 to 4095 for all voltage ranges |
| Output Ranges (Bipolar, Fixed):         | ±5V                              |
| Output Ranges (Bipolar, Programmable):  | ±1V to ±10V                      |
| Output Ranges (Unipolar, Fixed):        | 0-5V                             |
| Output Ranges (Unipolar, Programmable): | 0-1V to 0-10V                    |

### Digital I/O

|                   |                                                              |
| ----------------- | ------------------------------------------------------------ |
| Max Input Ports:  | 1 (1 byte or 8 bits), TTL compatible, no readback capability |
| Max Output Ports: | 1 (1 byte or 8 bits), TTL compatible                         |

Digital I/O lines on Diamond-MM-16-AT are fixed direction and do not require configuration prior to use.

### Diamond-MM-16-AT Universal Driver Functions

* [dscADAutoCal() ](../14.-universal-driver-apis/dscadautocal.md)
* [dscADCalVerify()](../14.-universal-driver-apis/dscadcalverify.md)&#x20;
* [dscADSample()](../14.-universal-driver-apis/dscadsample.md)&#x20;
* [dscADSampleInt() ](../14.-universal-driver-apis/dscadsampleint.md)
* [dscADScan()](../14.-universal-driver-apis/dscadscan.md)&#x20;
* [dscADScanInt() ](../14.-universal-driver-apis/dscadscanint.md)
* [dscADSetChannel() ](../14.-universal-driver-apis/dscadsetchannel.md)
* [dscADSetSettings() ](../14.-universal-driver-apis/dscadsetsettings.md)
* [dscClearUserInterruptFunction() ](../14.-universal-driver-apis/dscclearuserinterruptfunction.md)
* [dscCounterDirectSet() ](../14.-universal-driver-apis/dsccounterdirectset.md)
* [dscCounterRead()](../14.-universal-driver-apis/dsccounterread.md)&#x20;
* [dscCounterSetRate() ](../14.-universal-driver-apis/dsccountersetrate.md)
* [dscCounterSetRateSingle() ](../14.-universal-driver-apis/dsccountersetratesingle.md)
* [dscDAAutoCal() ](../14.-universal-driver-apis/dscdaautocal.md)
* [dscDACalVerify() ](../14.-universal-driver-apis/dscdacalverify.md)
* [dscDAConvert()](../14.-universal-driver-apis/dscdaconvert.md)&#x20;
* [dscDAConvertScan()](../14.-universal-driver-apis/dscdaconvertscan.md)&#x20;
* [dscDIOClearBit() ](../14.-universal-driver-apis/dscdioclearbit.md)
* [dscDIOInputBit() ](../14.-universal-driver-apis/dscdioinputbit.md)
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOOutputBit()](../14.-universal-driver-apis/dscdiooutputbit.md)&#x20;
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOSetBit() ](../14.-universal-driver-apis/dscdiosetbit.md)
* [dscGetEEPROM() ](../14.-universal-driver-apis/dscgeteeprom.md)
* [dscGetReferenceVoltages() ](../14.-universal-driver-apis/dscgetreferencevoltages.md)
* [dscGetStatus() ](../14.-universal-driver-apis/dscgetstatus.md)
* [dscSetEEPROM() ](../14.-universal-driver-apis/dscseteeprom.md)
* [dscSetReferenceVoltages() ](../14.-universal-driver-apis/dscsetreferencevoltages.md)
* [dscSetUserInterruptFunction() ](../14.-universal-driver-apis/dscsetuserinterruptfunction.md)
* [dscUserInt()](../14.-universal-driver-apis/dscuserint.md)
