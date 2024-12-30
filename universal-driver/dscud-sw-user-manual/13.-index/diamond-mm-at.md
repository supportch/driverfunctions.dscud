---
description: This product is supported for DSCUD 8.0 and above.
---

# Diamond-MM-AT

### Board Initialization

To use the DMM-AT board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_DMM. This is shown in the example below.

```c
dscInitBoard( DSC_DMM , &dsccb, &board );
```

### Analog Input

|                                                     |                                                  |
| --------------------------------------------------- | ------------------------------------------------ |
| Max Input Channels:                                 | 16 (single-ended) or 8 (differential)            |
| A/D Resolution:                                     | 12 bits (1/4096 of full-scale)                   |
| Data range:                                         | 0 to 4095 for all voltage ranges                 |
| Input Ranges (Bipolar):                             | ±10V, ±5V, ±2.5V, ±1V, ±0.5V, or Custom          |
| Input Ranges (Unipolar):                            | 0-10V, 0-5V, 0-2.5V, 0-1V, or Custom             |
| Supported Conversion Triggers:                      | Software, Internal Clock, or External TTL Signal |
| Maximum Conversion Rate (Software Command):         | 2,000 (approx.) samples per second               |
| Maximum Conversion Rate (Interrupt Routine w/FIFO): | 100,000 samples per second                       |
| FIFO:                                               | 512 samples with fixed threshold of 256          |

This board supports the following programmable input ranges and resolutions:

{% tabs %}
{% tab title="A/D Ranges" %}
| Code | Range | ADBU | G1 | G0 | Input Range     | Resolution (1 LSB) |
| ---- | ----- | ---- | -- | -- | --------------- | ------------------ |
| 0    | 0     | 0    | 0  | 0  | ±5V             | 2.44mV             |
| 1    | 0     | 0    | 0  | 1  | ±2.5V           | 1.22mV             |
| 2    | 0     | 0    | 1  | 0  | ±1.25V          | 0.61mV             |
| 3    | 0     | 0    | 1  | 1  | ±0.625V         | 0.305mV            |
| 4    | 0     | 1    | 0  | 0  | 0 - 10V         | 2.44mV             |
| 5    | 0     | 1    | 0  | 1  | 0 - 5V          | 1.22mV             |
| 6    | 0     | 1    | 1  | 0  | 0 - 2.5V        | 0.61mV             |
| 7    | 0     | 1    | 1  | 1  | 0 - 1.25V       | 0.305mV            |
| 8    | 1     | 0    | 0  | 0  | ±10V            | 4.88mV             |
| 9    | 1     | 0    | 0  | 1  | ±5V             | 2.44mV             |
| 10   | 1     | 0    | 1  | 0  | ±2.5V           | 1.22mV             |
| 11   | 1     | 0    | 1  | 1  | ±1.25V          | 0.61mV             |
| 12   | 1     | 1    | 0  | 0  | Invalid Setting | -                  |
| 13   | 1     | 1    | 0  | 1  | Invalid Setting | -                  |
| 14   | 1     | 1    | 1  | 0  | Invalid Setting | -                  |
| 15   | 1     | 1    | 1  | 1  | Invalid Setting | -                  |
{% endtab %}
{% endtabs %}

NOTE: Ranges 9 through 11 are identical to ranges 0 through 2.

### Analog Output

|                               |                                |
| ----------------------------- | ------------------------------ |
| Max Output Channels:          | 2                              |
| D/A Resolution:               | 12 bits (1/4096 of full-scale) |
| Data range:                   | 0 to 4095                      |
| Output Ranges (Fixed):        | 0-5V                           |
| Output Ranges (Programmable): | 0-1V to 0-10V                  |

### Digital I/O

|                   |                                                              |
| ----------------- | ------------------------------------------------------------ |
| Max Input Ports:  | 1 (1 byte or 8 bits), TTL compatible, no readback capability |
| Max Output Ports: | 1 (1 byte or 8 bits), TTL compatible                         |

Digital I/O lines on Diamond-MM-AT are fixed direction and do not require configuration prior to use.

### Diamond-MM-AT Universal Driver Functions

* [dscADAutoCal() ](../14.-universal-driver-apis/dscadautocal.md)
* [dscADCalVerify() ](../14.-universal-driver-apis/dscadcalverify.md)
* [dscADSample() ](../14.-universal-driver-apis/dscadsample.md)
* [dscADSampleInt() ](../14.-universal-driver-apis/dscadsampleint.md)
* [dscADScan() ](../14.-universal-driver-apis/dscadscan.md)
* [dscADScanInt() ](../14.-universal-driver-apis/dscadscanint.md)
* [dscADSetChannel() ](../14.-universal-driver-apis/dscadsetchannel.md)
* [dscADSetSettings() ](../14.-universal-driver-apis/dscadsetsettings.md)
* [dscClearUserInterruptFunction() ](../14.-universal-driver-apis/dscclearuserinterruptfunction.md)
* [dscCounterDirectSet() ](../14.-universal-driver-apis/dsccounterdirectset.md)
* [dscCounterRead() ](../14.-universal-driver-apis/dsccounterread.md)
* [dscCounterSetRate() ](../14.-universal-driver-apis/dsccountersetrate.md)
* [dscCounterSetRateSingle() ](../14.-universal-driver-apis/dsccountersetratesingle.md)
* [dscDAAutoCal() ](../14.-universal-driver-apis/dscdaautocal.md)
* [dscDACalVerify() ](../14.-universal-driver-apis/dscdacalverify.md)
* [dscDAConvert()](../14.-universal-driver-apis/dscdaconvert.md)&#x20;
* [dscDAConvertScan()](../14.-universal-driver-apis/dscdaconvertscan.md)&#x20;
* [dscDIOClearBit() ](../14.-universal-driver-apis/dscdioclearbit.md)
* [dscDIOInputBit()](../14.-universal-driver-apis/dscdioinputbit.md)&#x20;
* [dscDIOInputByte()](../14.-universal-driver-apis/dscdioinputbyte.md)&#x20;
* [dscDIOOutputBit() ](../14.-universal-driver-apis/dscdiooutputbit.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOSetBit() ](../14.-universal-driver-apis/dscdiosetbit.md)
* [dscGetEEPROM() ](../14.-universal-driver-apis/dscgeteeprom.md)
* [dscGetReferenceVoltages() ](../14.-universal-driver-apis/dscgetreferencevoltages.md)
* [dscGetStatus() ](../14.-universal-driver-apis/dscgetstatus.md)
* [dscSetEEPROM() ](../14.-universal-driver-apis/dscseteeprom.md)
* [dscSetReferenceVoltages() ](../14.-universal-driver-apis/dscsetreferencevoltages.md)
* [dscSetUserInterruptFunction() ](../14.-universal-driver-apis/dscsetuserinterruptfunction.md)
* [dscUserInt()](../14.-universal-driver-apis/dscuserint.md)
