---
description: >-
  This page describes the DAC section of the DAQ subsystem available on Athena
  IV.
---

# Digital to Analog Converter

## 13.3 Digital-to-Analog Output Ranges and Resolution

### 13.3.1 Description

Athena IV uses a 4-channel 12-bit D/A converter (DAC) to provide four analog outputs. A 12-bit DAC can generate output voltages with the precision of a 12-bit binary number. The maximum value of a 12-bit binary number is 212 - 1, or 4095, so the full range of numerical values that the DACs support is 0 - 4095. The value 0 always corresponds to the lowest voltage in the output range, and the value 4095 always corresponds to the highest voltage minus 1 LSB. The theoretical top end of the range corresponds to an output code of 4096 which is impossible to achieve.

**NOTE:** _In this manual, the terms analog output, D/A, and DAC are all used interchangeably to mean the conversion of digital data originating from the Athena IV SBC to an analog signal terminating at an external source._

### 13.3.2 Resolution

The resolution is the smallest possible change in output voltage. For a 12-bit DAC the resolution is 1/(212), or 1/4096, of the full-scale output range. This smallest change results from an increase or decrease of 1 in the D/A code, so this change is referred to as 1 least significant bit (1 LSB). The value of this LSB is calculated as follows.

1 LSB = Output voltage range / 4096&#x20;

Example:&#x20;

For, Output range = 0-10V,&#x20;

**Output voltage range = 10V – 0V = 10V**&#x20;

Therefore, 1 LSB = 10V / 4096 = 2.44mV&#x20;

Example: For, Output range = 10V;&#x20;

**Output voltage range = 10V – (-10V) = 20V**&#x20;

Therefore,&#x20;

**1 LSB = 20V / 4096 = 4.88mV**

### **13.3.3** Output Range Selection&#x20;

Jumper block J26 is used to select the DAC output range. The DACs can be configured for 0-10V or 10V. Two parameters are configured:&#x20;

* unipolar/bipolar mode
* power-up/reset clear mode

In most cases, for unipolar mode configure the board to reset to zero scale, and for bipolar mode configure the board for reset to mid-scale. In each case, the DACs reset to 0V.

### 13.3.4 D/A Conversion Formulas and Tables&#x20;

The formulas below explain how to convert between D/A codes and output voltages.&#x20;

**D/A Conversion Formulas for Unipolar Output Ranges**&#x20;

**Output voltage = (D/A code / 4096)  \* Reference voltage**

&#x20;**D/A code = (Output voltage / Reference voltage) \* 4096**&#x20;

Example:

&#x20;For,&#x20;

Output range in unipolar mode = 0 – 10V, and,&#x20;

Full-scale range = 10V – 0V = 10V,&#x20;

if,&#x20;

Desired output voltage = 2.000V,&#x20;

**D/A code = 2.000V / 10V  \* 4096 = 819.2 => 819**&#x20;

**NOTE**_: The output code is always an integer._&#x20;

_For the unipolar output range 0-10V, 1 LSB = 1/4096_ 10V = 2.44mV.&#x20;

The following table illustrates the relationship between D/A code and output voltage for a unipolar output range (VREF = Reference voltage):

| **D/A Code** | **Output Voltage Symbolic Formula** | **Output Voltage for 0-10V Range** |
| ------------ | ----------------------------------- | ---------------------------------- |
| 0            | 0V                                  | 0.0000V                            |
| 1            | 1 LSB (VREF / 4096)                 | 0.0024V                            |
| ...          | ...                                 | ...                                |
| 2047         | VREF / 2 - 1 LSB                    | 4.9976V                            |
| 2048         | VREF / 2                            | 5.0000V                            |
| 2049         | VREF / 2 + 1 LSB                    | 5.0024V                            |
| ...          | ...                                 | ...                                |
| 4095         | VREF - 1 LSB                        | 9.9976V                            |

**D/A Conversion Formulas for Bipolar Output Ranges**

&#x20;**Output voltage = ((D/A code – 2048) / 2048) &#x20;**_**\***&#x20;_&#x20;_**Output reference**_&#x20;

**D/A code = (Output voltage / Output reference)  \* 2048 + 2048**&#x20;

Example:&#x20;

For, Output range in bipolar mode = ±10V and,&#x20;

Full-scale range = 10V – (-10V) = 20V&#x20;

if,&#x20;

Desired output voltage = 2.000V&#x20;

**D/A code = 2V / 10V&#x20;**_**\* 2048 + 2048 = 2457.6 => 2458**_&#x20;

For the bipolar output range 10V,&#x20;

**1 LSB = 1/4096  20V, or 4.88mV**

The following table illustrates the relationship between D/A code and output voltage for a bipolar output range (VREF = Reference voltage):

| **D/A Code** | **Output Voltage Symbolic Formula** | **Output Voltage for 10V Range** |
| ------------ | ----------------------------------- | -------------------------------- |
| 0            | -VREF                               | -10.0000V                        |
| 1            | VREF + 1 LSB                        | -9.9951V                         |
| ...          | ...                                 | ...                              |
| 2047         | -1 LSB                              | -0.0049V                         |
| 2048         | 0                                   | 0.0000V                          |
| 2049         | +1 LSB                              | 0.0049V                          |
| ...          | ...                                 | ...                              |
| 4095         | VREF - 1 LSB                        | 9.9951V                          |

### 13.3.5 Generating an Analog Output&#x20;

There are three steps involved in performing a D/A conversion, or generating an analog output. Each step is described in more detail, below. The descriptions use direct programming instead of driver software.&#x20;

1. Compute the D/A code for the desired output voltage
2. Write the value to the selected output channel
3. Wait for the D/A to update

### 13.3.6 Compute the D/A Code for the Desired Output Voltage

Use the formulas in the preceding section to compute the D/A code required to generate the desired voltage.&#x20;

**NOTE:** _The DAC cannot generate the actual full-scale reference voltage; to do so would require an output code of 4096, which is not possible with a 12-bit number. The maximum output value is 4095. Therefore, the maximum possible output voltage is always 1 LSB less than the full-scale reference voltage._&#x20;

### 13.3.7 Write the Value to the Selected Output Channel Registers

&#x20;Use the following formulas to compute the LSB and MSB values.&#x20;

**LSB = D/A Code & 255 ; keep only the low 8 bits**&#x20;

**MSB = int(D/A code / 256) ;strip off low 8 bits, keep 4 high bits**&#x20;

Example:

&#x20;For,&#x20;

**Output code = 1776**&#x20;

**Compute, LSB = 1776 & 255 = 240 (0xF0)** and&#x20;

**MSB = int(1776 / 256) = int(6.9375) = 6**&#x20;

The LSB is an 8-bit number in the range 0-255. The MSB is a 4-bit number in the range 0-15.&#x20;

The MSB is always rounded down. The truncated portion is accounted for by the LSB.&#x20;

Write these values to the selected channel. The LSB is written to Base+6. The MSB and channel number are written to Base+7 (MSB = bits 0-3, channel number,0-3 = bits 6-7).&#x20;

```
outp(Base+6, LSB);
 outp(Base+7, MSB + channel << 6)
```

### 13.3.8 Wait for the D/A to Update&#x20;

Writing the MSB and channel number to Base+7 starts the D/A update process for the selected channel. The update process requires approximately 30 microseconds to transmit the data serially to the D/A chip and update the D/A circuit in the chip. During this period, no attempt should be made to write to any other channel in the D/A through addresses Base+6 or Base+7.&#x20;

The status bit DACBUSY (Base+3, bit 4) indicates if the D/A is busy updating (1) or idle (0). After writing to the D/A, monitor DACBUSY until it is zero before continuing with the next D/A operation.

### 13.3.9 Analog Circuit Calibration

The Athena IV data acquisition circuit contains an advanced autocalibration circuit that can maintain the accuracy of both A/D and D/A circuits to within the specified tolerances regardless of time and temperature. Autocalibration is supported in the Diamond Systems Universal Driver software included with the SBC.&#x20;

The autocalibration circuit uses an ultra-stable +5V reference voltage IC as the source for its calibration. Both A/D and D/A circuits are calibrated in the analog domain by using a series of 8-bit “TrimDACs” to adjust the offset and gain settings of the circuits. The data values driving the DACs are stored in an EEPROM and are loaded automatically each time the board powers up.&#x20;

During the autocalibration process, the SBC measures the on-board reference and calibrate the A/D circuit by adjusting the TrimDACs to achieve the best accuracy. Once the A/D circuit is calibrated, the D/A circuit is calibrated by routing the D/A outputs into the A/D converter and adjusting them as well. The new calibration values for the TrimDACs are stored back into the EEPROM so they can be automatically recalled thereafter.&#x20;

A unique feature of Diamond’s autocalibration process is that each analog input range is individually calibrated for optimum performance. Analog amplifier circuits with 16-bit accuracy exhibit gain and offset errors that vary depending on the gain setting. The settings that work best for one range may not be sufficient to calibrate another. If a circuit is calibrated for maximum accuracy in a particular input range, such as +/-5V, changing the input range to +/-10V or 0-2.5V may introduce errors that exceed the resolution of a 16-bit measurement and would require calibration again.&#x20;

To counteract this phenomenon, Diamond’s autocalibration circuit provides for a separate complete set of calibration settings for each analog input range. During the autocalibration process, each range is calibrated one at a time, and its set of calibration settings is stored in a separate area of the EEPROM’s memory. One of these ranges is identified as the “boot range”, and this range’s calibration values are the ones that are automatically recalled during power-up. You have the option of specifying the boot range, which should be chosen as the range most commonly used in your application. When you change the input range, you have the option of loading the calibration values for the new input range to maintain optimum accuracy of your measurements.&#x20;

The autocalibration process is triggered with a single function call in the Diamond Universal Driver software. The process takes about 10-20 seconds to calibrate the complete set of analog input ranges and about the same time for the D/A circuit. Autocalibration can easily be incorporated into your application program, so that you can calibrate the data acquisition circuit as often as necessary while your system is running.
