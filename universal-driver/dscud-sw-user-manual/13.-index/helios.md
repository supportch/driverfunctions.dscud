---
description: This product is supported for DSCUD 8.0 and above.
---

# Helios

### Overview

Helios's Data Acquisition circuitry is similar to that on Athena-II but some of the registers for controlling the behavior of the circuit are different on Helios from Athena II.

The Universal Driver handles the differences. Below are some of the major differences in the Helios board.&#x20;

1\. Watchdog Timer support.&#x20;

2\. Additional DIO ports available in Helios.&#x20;

3\. DA modes are software programmable.&#x20;

4\. DA channels can be individually programmed for unique range settings.&#x20;

In case of Helios board, all the AD and DA settings are only software programmable. Unlike the previous boards, jumpers cannot be used to perform the AD / DA mode and polarity settings.

### Board Initialization

To use the Helios board in an application using the UD, the dscInitBoard function should use the board macro DSC\_HELIOS. This is shown in the example below... The base address should be 0x280 ( or whatever is set in the BIOS of the board) and the default IRQ to use is IRQ 5.

```
dscInitBoard(DSC_ZETA, &dsccb, &board );
```

&#x20;It is highly recommended that the dsccb structure be memset to 0 in the application before calling the dscInitBoard API.

```
memset ( &dsccb , 0 , sizeof ( DSCCB ) ); 

```

The Helios board also uses the DAC\_Config element available in the DSCCB structure to force 16 bit DAC operation. To use the 16 bit DAC mode of the Helios board, the DAC\_Config element of the DSCCB structure must be set to 1 before calling the dscInitBoard API.&#x20;

dsccb.DAC\_Config = 1 ; // for 16 bit mode DAC.&#x20;

Currently Helios boards have only 12 bit DAC available and thus it is advisable to set the DAC\_Config to 0.

NOTE: For making the interrupt based operations work on Helios board, the IRQ5 MUST be set to Reserved in the BIOS.

### Analog Input

|                                                   |                                                                           |
| ------------------------------------------------- | ------------------------------------------------------------------------- |
| Max Input Channels:                               | 16 (single-ended) or 8 (differential)                                     |
| A/D Resolution:                                   | 16 bits (1/65536 of full-scale)                                           |
| Data range:                                       | -32768 to +32767 for all voltage ranges                                   |
| Input Ranges (Bipolar):                           | ±10V, ±5V, ±2.5, ±1.25                                                    |
| Input Ranges (Unipolar):                          | 0-10V, 0-5V, 0-2.5V or 0-1.25V                                            |
| Supported Conversion Triggers:                    | Software, Internal Clock, or External TTL Signal                          |
| Maximum Conversion Rate (Software Command):       | approx. 20,000 samples per second, depending on code and operating system |
| Maximum Conversion Rate(Interrupt Routine w/FIFO) | 100,000 samples per second                                                |

**FIFO:**&#x20;

1. 48 samples with programmable threshold in standard mode.&#x20;
2. Upto 2048 in Enhanced FIFO mode.

In the enhanced FIFO mode, it is recommended to set the FIFO threshold to 1024 samples by setting the FIFO threshold register Base + 5 with a value of 0x80. The FIFO threshold register at location Base + 5 of the Helios board, contains the threshold for the enhanced mode. The threshold is an 11 bit number as the maximum FIFO depth available in Helios is 2048. Thus to set the threshold value of 11 bit in an 8 bit register, the threshold value is programmed as 8 sample blocks. The universal driver takes care of the conversion.

For example, to set a FIFO threshold of 1024, the Universal Driver will write a value of 0x80 to the register.

{% tabs %}
{% tab title="A/D Ranges" %}
| Polarity | G1 | G0 | Input Range | Resolution (1 LSB) |
| -------- | -- | -- | ----------- | ------------------ |
| Bipolar  | 0  | 0  | ±10V        | 305μV              |
| Bipolar  | 0  | 1  | ±5V         | 153μV              |
| Bipolar  | 1  | 0  | ±2.5V       | 76μV               |
| Bipolar  | 1  | 1  | ±1.25V      | 38μV               |
| Unipolar | 0  | 0  | 0 - 10V     | 153μV              |
| Unipolar | 0  | 1  | 0 - 5V      | 76μV               |
| Unipolar | 1  | 0  | 0 - 2.5V    | 38μV               |
| Unipolar | 1  | 1  | 0 - 1.25V   | 19μV               |
{% endtab %}
{% endtabs %}

### Analog Output

|                         |                                  |
| ----------------------- | -------------------------------- |
| Max Output Channels:    | 4                                |
| D/A Resolution:         | 12 bits (1/4096 of full-scale)   |
| Data range:             | 0 to 4095 for all voltage ranges |
| Bipolar Output Ranges:  | ±10V                             |
| Unipolar Output Ranges: | 0-10V                            |

The Helios board provides the following programmable DA modes. The DA modes can be set using a new API function called dscDASetSettings ().

{% tabs %}
{% tab title="D/A Ranges" %}
| G1 | G0 | DAPOL | Description                        |
| -- | -- | ----- | ---------------------------------- |
| 0  | 0  | 0     | 5V Span ( 0 to +5V Unipolar )      |
| 0  | 0  | 1     | 5V Span ( -2.5V to +2.5V Bipolar ) |
| 0  | 1  | 0     | 10V Span ( 0 10 +10V Unipolar )    |
| 0  | 1  | 1     | 10V Span ( -5V to +5V Bipolar )    |
| 1  | 0  | 1     | NOT USED                           |
| 1  | 0  | 1     | 20V Span ( -10V to +10V Bipolar )  |
| 1  | 1  | 1     | D/A converter shut down            |
| 1  | 1  | 0     | NOT USED                           |
{% endtab %}
{% endtabs %}

### Digital I/O

Helios supports 5 DIO ports. All the DIO ports are bi-directional, programmable in 8-bit groups, TTL-compatible and are similar to 82C55 Digital I/O ports on AthenaII. All the ports require the port direction to be set with dscDIOSetConfig before use. The value of 0x00 is used for the port to be an output port while 0xFF configures the port as an input port.&#x20;

The Helios board supports 3 DIO ports which are 82C55 based ports provided by the on-board FPGA. There are 2 more DIO ports made available to the user which are directly provided by the CPU.

All DIO lines power-up in input mode and have readback capability.

### Helios Universal Driver Functions

* [dscADAutoCal() ](../14.-universal-driver-apis/dscadautocal.md)
* [dscADCalVerify()](../14.-universal-driver-apis/dscadcalverify.md)&#x20;
* [dscADSample() ](../14.-universal-driver-apis/dscadsample.md)
* [dscADSampleInt() ](../14.-universal-driver-apis/dscadsampleint.md)
* [dscCancelOp()](../14.-universal-driver-apis/dsccancelop.md)
* [dscADScan() ](../14.-universal-driver-apis/dscadscan.md)
* [dscADScanInt() ](../14.-universal-driver-apis/dscadscanint.md)
* [dscADSetSettings() ](../14.-universal-driver-apis/dscadsetsettings.md)
* [dscADSetChannel()](../14.-universal-driver-apis/dscadsetchannel.md)
* [dscSetCalMux()](../14.-universal-driver-apis/dscsetcalmux.md)
* [dscGetReferenceVoltages()](../14.-universal-driver-apis/dscgetreferencevoltages.md)
* [dscSetReferenceVoltages()](../14.-universal-driver-apis/dscsetreferencevoltages.md)
* [dscDAConvert() ](../14.-universal-driver-apis/dscdaconvert.md)
* [dscDAConvertScan() ](../14.-universal-driver-apis/dscdaconvertscan.md)
* [dscDASetSettings() ](../14.-universal-driver-apis/dscdasetsettings.md)
* [dscDAAutoCal()](../14.-universal-driver-apis/dscdaautocal.md)
* [dscDACalVerify()](../14.-universal-driver-apis/dscdacalverify.md)
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOSetConfig()](../14.-universal-driver-apis/dscdiosetconfig.md)
* [dscLEDTest() ](../14.-universal-driver-apis/dscledtest.md)
* [dscUserInt()](../14.-universal-driver-apis/dscuserint.md)
* [dscSetUserInterruptFunction()](../14.-universal-driver-apis/dscsetuserinterruptfunction.md)
* [dscGetStatus()](../14.-universal-driver-apis/dscgetstatus.md)
* [dscClearUserInterruptFunction()](../14.-universal-driver-apis/dscclearuserinterruptfunction.md)
* [dscWatchdogTrigger()](../14.-universal-driver-apis/dscwatchdogtrigger.md)
* [dscSetTrimDac()](../14.-universal-driver-apis/dscsettrimdac.md)
* [dscSetEEPRO&#x4D;**()**](../14.-universal-driver-apis/dscseteeprom.md)
* [dscGetEEPROM()](../14.-universal-driver-apis/dscgeteeprom.md)

