---
description: This product is supported for DSCUD 8.0 and above.
---

# Diamond-MM-32DX-AT

### Overview

DMM32DX-AT is backwards compatible with DMM32X-AT. However the DMM32DX-AT has many enhanced features that improve performance and make it more attractive for certain applications. Some of the features are a 1024 sample FIFO (2048 upon request), 250 KHz max sample rate, auto auto-calibration, D/A wave form generator, and programmable FPGA. DMM32DX-AT also has the capability to receive commands via RS232.

### Board Initialization

To use the DMM-32DX-AT board in an appllication using the UD, the dscInitBoard function should use the board macro DSC\_DMM32DX. This is shown in the example below.

Apart from the regular parameters filled in for the DSSCB structure, for DMM32DX, an additional member needs to be filled called DAC\_Config.

```c
dsccb.DAC_Config = 1 ; // for 16 bit DAC usage or 0 for 12 bit DAC usage.
```

This member will let the universal driver know the type of DAC usage intended by the user. If the user wants to use only 12 bit operation ( even though the DAC chip installed is 16 bit), this parameter should be set to 0. If the user desires to use the extended mode 16 bit DAC functionality, this member should be set to 1.

```c
dscInitBoard( DSC_DMM32DX , &dsccb, &board );
```

### Analog Input

|                                                     |                                                                              |
| --------------------------------------------------- | ---------------------------------------------------------------------------- |
| Max Input Channels:                                 | 32 (single-ended), 24 (16/8 single-ended/differential), or 16 (differential) |
| A/D Resolution:                                     | 16 bits (1/65536 of full-scale)                                              |
| Data range:                                         | -32768 to +32767 for all voltage ranges                                      |
| Input Ranges (Bipolar):                             | ±10V, ±5V, ±2.5V, ±1.25V, or ±0.625V                                         |
| Input Ranges (Unipolar):                            | 0-10V, 0-5V, 0-2.5V, or 0-1.25V                                              |
| Supported Conversion Triggers:                      | Software, Internal Clock, or External TTL Signal                             |
| Maximum Conversion Rate (Software Command):         | system-dependent, up to 100,000 per second                                   |
| Maximum Conversion Rate (Interrupt Routine w/FIFO): | 250,000 samples per second                                                   |
| FIFO:                                               | 1024 samples (2048 upon request) with programmable threshold                 |

This board supports the following programmable input ranges and resolutions:

{% tabs %}
{% tab title="A/D Ranges" %}
| Code | Range | ADBU | G1 | G0 | Input Range     | Resolution (1 LSB) |
| ---- | ----- | ---- | -- | -- | --------------- | ------------------ |
| 0    | 0     | 0    | 0  | 0  | ±5V             | 153μV              |
| 1    | 0     | 0    | 0  | 1  | ±2.5V           | 76μV               |
| 2    | 0     | 0    | 1  | 0  | ±1.25V          | 38μV               |
| 3    | 0     | 0    | 1  | 1  | ±0.625V         | 19μV               |
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
| 15   | 1     | 1    | 1  | 1  | 0 - 1.25V       | 19μV               |
{% endtab %}
{% endtabs %}

NOTE: Ranges 9 through 11 are identical to ranges 0 through 2.

### Analog Output

|                           |                                   |
| ------------------------- | --------------------------------- |
| Max Output Channels:      | 4 D/A                             |
| Resolution:               | 12 bits (1/4096 of full-scale)    |
| Data range:               | 0 to 4095 for all voltage ranges  |
| Output Ranges (Bipolar):  | ±2.5V, ±5V, ±10V, or programmable |
| Output Ranges (Unipolar): | 0-5V, 0-10V, or programmable      |

### Digital I/O

|            |                                                                                                                                                                                                                                                                                                                                                                             |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Max Ports: | 3 (bi-directional, programmable in 8-bit groups, TTL-compatible) similar to 82C55 Digital I/O ports on Diamond-MM-32-AT require direction to be set with dscDIOSetConfig() before use. All DIO lines power-up in input mode and have readback capability. All DIO lines have 4.7K Ohm pull resistors that can be configured for all pull-up or all pull-down with a jumper. |

### Universal Driver API Notes

For these functions DMM32X-AT has the following restrictions

**dscADSampleInt, dscADScanInt**&#x20;

1\. FIFO threshold (dscaioint.fifo\_depth) must be a multiple of the number of channels&#x20;

2\. Num\_conversions (dscaioint.num\_conversions) must be a multiple of fifo threshold&#x20;

3\. FIFO threshold (dscaioint.fifo\_depth) must be an even number between 0 to 1022 (or 0 to 2046 for 2048 size FIFO)

### Diamond-MM-32DX-AT Universal Driver Functions

* [dscAACCommand() ](../14.-universal-driver-apis/dscaaccommand.md)
* [dscAACGetStatus() ](../14.-universal-driver-apis/dscaacgetstatus.md)
* [dscADAutoCal()](../14.-universal-driver-apis/dscadautocal.md)&#x20;
* [dscADCalVerify() ](../14.-universal-driver-apis/dscadcalverify.md)
* [dscADSample() ](../14.-universal-driver-apis/dscadsample.md)
* [dscADSampleInt () ](../14.-universal-driver-apis/dscadsampleint.md)
* [dscADScan()](../14.-universal-driver-apis/dscadscan.md)&#x20;
* [dscADScanInt() ](../14.-universal-driver-apis/dscadscanint.md)
* [dscADSetChannel() ](../14.-universal-driver-apis/dscadsetchannel.md)
* [dscADSetSettings()](../14.-universal-driver-apis/dscadsetsettings.md)&#x20;
* [dscClearUserInterruptFunction() ](../14.-universal-driver-apis/dscclearuserinterruptfunction.md)
* [dscCounterDirectSet() ](../14.-universal-driver-apis/dsccounterdirectset.md)
* [dscCounterRead()](../14.-universal-driver-apis/dsccounterread.md)&#x20;
* [dscCounterSetRate() ](../14.-universal-driver-apis/dsccountersetrate.md)
* [dscCounterSetRateSingle() ](../14.-universal-driver-apis/dsccountersetratesingle.md)
* [dscDAAutoCal() ](../14.-universal-driver-apis/dscdaautocal.md)
* [dscDACalVerify() ](../14.-universal-driver-apis/dscdacalverify.md)
* [dscDAConvert() ](../14.-universal-driver-apis/dscdaconvert.md)
* [dscDAConvertScan() ](../14.-universal-driver-apis/dscdaconvertscan.md)
* [dscDIOClearBit() ](../14.-universal-driver-apis/dscdioclearbit.md)
* [dscDIOInputBit() ](../14.-universal-driver-apis/dscdioinputbit.md)
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOOutputBit()](../14.-universal-driver-apis/dscdiooutputbit.md)&#x20;
* [dscDIOOutputByte()](../14.-universal-driver-apis/dscdiooutputbyte.md)&#x20;
* [dscDIOSetBit() ](../14.-universal-driver-apis/dscdiosetbit.md)
* [dscDIOSetConfig() ](../14.-universal-driver-apis/dscdiosetconfig.md)
* [dscEnhancedFeaturesEnble() ](../14.-universal-driver-apis/dscenhancedfeaturesenble.md)
* [dscGetEEPROM()](../14.-universal-driver-apis/dscgeteeprom.md)&#x20;
* [dscGetReferenceVoltages() ](../14.-universal-driver-apis/dscgetreferencevoltages.md)
* [dscGetStatus()](../14.-universal-driver-apis/dscgetstatus.md)&#x20;
* [dscSetEEPROM() ](../14.-universal-driver-apis/dscseteeprom.md)
* [dscSetReferenceVoltages() ](../14.-universal-driver-apis/dscsetreferencevoltages.md)
* [dscSetUserInterruptFunction() ](../14.-universal-driver-apis/dscsetuserinterruptfunction.md)
* [dscUserInt() ](../14.-universal-driver-apis/dscuserint.md)
* [dscWGBufferSet() ](../14.-universal-driver-apis/dscwgbufferset.md)
* [dscWGCommand()](../14.-universal-driver-apis/dscwgcommand.md)&#x20;
* [dscWGConfigSet()](../14.-universal-driver-apis/dscwgconfigset.md)

### Limitation

Current UD driver doesn't Support 16- bit AD/DA read/write operations.
