# D/A Functions

### **BYTE SATURNDASetSettings(BoardInfo\* bi, int Channel, int Range, int OverRange, int ClearEnable, int LoadCal);**

This function is designed to work with the AD5755 / AD5755-1 D/A converter. This function configures the following settings for a single output channel.

* Output range set via input parameter
* Overrange is enabled/disabled via input parameter
* Clear enable/disable set via input parameter
* Output is enabled
* External resistor is selected (to match board physical configuration)
* DC/DC converter is enabled
* Calibration settings may optionally be recalled

All D/A channels are configured for 0-5V during board initialization, and the unipolar calibration settings are loaded into the D/A chips at power-up or reset. If the application requires any other ranges, then each channel that uses a different range must have its settings configured independently by calling this function prior to using the channel. The driver should keep track of the output range set for each channel in order to know what is the 0V output code for each channel.

The proper method for changing the output range on the AD5755 DAC is as follows:

1\.       Set output to 0V / 0mA code (0 or midscale)

2\.       Write to DAC control register with the new output range; INT\_ENABLE = 1, DCDC = 1 (for current ranges), and OUTEN = 0 to disable the output

3\.       Recall calibration settings if desired or if a current output range is selected (4, 5, or 6)

4\.       Write the existing output value to the DAC data register

5\.       Write to DAC control register again with the new output range; INT\_ENABLE = 1, DCDC = 1 (for current ranges), and OUTEN = 1 to enable the output

Input parameters:

|              |     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------ | --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Channel      | int | 0-3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Range        | int | <p>0-6, see list:                                                                 0 = 0-5V</p><p>                                                                1 = 0-10V</p><p>                                                                2 = +/5V</p><p>                                                                3 = +/-10V</p><p>                                                                4 = 4-20mA</p><p>                                                                5 = 0-20mA</p><p>                                                                6 = 0-24mA</p> |
| Overrange    | int | <p>0 = disable overrange, range is as indicated above</p><p>                                                                1 = enable 20% overrange (for voltage ranges only, invalid for </p>                                                                                                                                                                                                                                                                                                                                                                                                   |
| ClearEnable  | int | 0 = disable clear on chip clear; 1 = enable clear on chip clear                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| LoadCal      | int | <p>0 = don’t load calibration values from EEPROM; 1 = load calibration values from EEPROM</p><p>                                                                (for current output ranges the calibration values are always reset)</p>                                                                                                                                                                                                                                                                                                                                                           |

This function operates as follows:

Set page = 1

&#x20;

If Range is 2 or 3 then Unibip = 1 else Unibip = 0

If Range is 2 or 3 then dacode = 0x8000 else dacode = 0x0000 // select midscale or zero scale 0

Write dacode to registers 0,1

MSB = Channel

Write MSB to register 2

Wait for DABUSY = 0 in register 7

Return timeout error if DABUSY does not return to 0 within the specified time limit

&#x20;

LSB = 0x10 + ClearEnable << 7 + OverRange << 3 + Range (Clear enable is bit 7, Overrange is bit 3)

Write LSB to register 0

CSB = 0x41

Write CSB to register 1

MSB = 0x1C + Channel

Write MSB to register 2

&#x20;

If LoadCal = 1 then:

&#x20;       If Range = 0-3 then:

&#x20;               Read EEPROM addresses (192 + Unibip \* 16 + Channel \* 4) and  (192 + Unibip \* 16 + Channel \* 4 + 1)

&#x20;               Build M register value from 2 bytes

&#x20;               Write M register value to DAC using SATURNSetGain()

&#x20;               // Wait for DABUSYn = 0 in register 7 (should not be needed)

&#x20;               // Return timeout error if DABUSY does not return to 0 within time limit (should not be needed)

&#x20;               Read EEPROM addresses (192 + Unibip \* 16 + Channel \* 4 + 2) and  (192 + Unibip \* 16 + Channel \* 4 + 3)

&#x20;               Build C register value from 2 bytes

&#x20;               Write C register value to DAC using SATURNSetOffset()

&#x20;               // Wait for DABUSYn = 0 in register 7 (should not be needed)

&#x20;               // Return timeout error if DABUSY does not return to 0 within time limit (should not be needed)

&#x20;

&#x20;       If Range = 4, 5, or 6 (current range) then:

&#x20;               Call  SATURNSetGain() with current channel and gain value = DefaultGain\*

&#x20;               Call  SATURNSetOffset() with current channel and offset value = DefaultOffset\*

&#x20;

\* DefaultGain and DefaultOffset should be in the SATURN.h file and should be set to default values of 0xFE00 and 0x8000 respectively. These values are subject to future change based on adjustment of the SATURN reference circuit.

&#x20;

Write previously loaded dacode to registers 0,1

MSB = Channel

Write MSB to register 2

Wait for DABUSYn = 0 in register 7

Return timeout error if DABUSY does not return to 0 within the specified time limit

&#x20;

LSB = 0x50 + ClearEnable << 7 + Overrange << 3 + Range (Clear enable is bit 7, Overrange is bit 3)

Write LSB to register 0

CSB = 0x41

Write CSB to register 1

MSB = 0x1C + Channel

Write MSB to register 2

&#x20;

Set page = 0

Exit

### **BYTE SATURNDASetSim(BoardInfo\* bi, int Simup);**

This function configures the board for simultaneous update or regular single-channel update mode.

Input parameters:

|       |     |                                                              |
| ----- | --- | ------------------------------------------------------------ |
| Simup | int | 0 = single-channel update mode, 1 = simultaneous update mode |

This function operates as follows:

Set page = 1

Write Simup to register 5 bit 0 (DASIM)

Set page = 0

Exit

### **BYTE SATURNDAConvert(BoardInfo\* bi, int Channel, unsigned DACode);**

This function outputs a value to a single D/A channel. The output range must be previously set with DASetSettings(). If the board is not set for simultaneous update mode (DASIM = 0), the channel will be updated immediately after the DAC internal calibration circuit is finished. If the board is set for simultaneous update mode (DASIM = 1), the channel will not be updated, and a separate update command must be executed.&#x20;

The software must keep track of the output code written to each channel since this is needed when changing the output range.

Input parameters:

|          |          |         |
| -------- | -------- | ------- |
| Channels | int      | 0-3     |
| DACode   | unsigned | 0-65535 |

In the description below, n = A for channels 0-3, B for channels 4-7, C for channels 8-11, or D for channels 12-15.

&#x20;

This function operates as follows:

Set page = 1

Wait for DABUSY = 0 in register 7 // must wait for any previous operation to finish before writing again

Return timeout error if DABUSY does not return to 0 within the specified time limit

Write the D/A code to registers 0 and 1

MSB = Channel

Write MSB to register 2

Read DASIM bit (register 5 bit 0)

If DASIM = 1 then exit // simultaneous update mode is in effect so don’t update now

Wait for DABUSY = 0 in register 7 // must wait for calibration circuit to finish before updating DAC

Return timeout error if DABUSY does not return to 0 within the specified time limit

Write 1 to command bit DALDn in register 6 to update DAC

Set page = 0

Exit

### **BYTE SATURNDAConvertScan(BoardInfo\* bi, int\* ChannelSelect, unsigned\* DACodes);**

This function outputs multiple values to multiple D/A channels. The output ranges must be previously set with DASetSettings(). If the board is not set for simultaneous update mode (DASIM = 0), each channel will be updated immediately by the hardware after being written to. If the board is set for simultaneous update mode (DASIM = 1), the channel will not be updated, and a separate update command must be executed. This function simply calls SATURNDAConvert() once for each channel to be updated. It is mostly used for simultaneous mode operation where all channels will be updated at the same time after all data is written.

Input parameters:

|               |             |                                                  |
| ------------- | ----------- | ------------------------------------------------ |
| ChannelSelect | int \*      | 0 = don’t update channel n, 1 = update channel n |
| DACodes       | unsigned \* | 0-65535 for each channel to be updated           |

This function operates as follows:

For i = 0 to 15

If ChannelSelect\[i] = 1 then call SATURNDAConvert() with Channel = i and DACode = DACodes\[i]

Next i

Set page = 1

Read DASIM bit (register 5 bit 0)

If DASIM = 0 then exit // simultaneous update mode is not in effect so DACs will be updated already

Wait for DABUSY = 0 in register 7 // must wait for all previous operations to finish before updating DACs

Return timeout error if DABUSY does not return to 0 within the specified time limit

Write 0x80 to register 6 // DASIMUP command

Set page = 0

Exit

### **BYTE SATURNDAFunction(BoardInfo\* bi, unsigned DAData, int DACommand);**

This function enables the programmer to control the D/A chip directly to implement special functions that are not supported by other DSCUD functions. This function is general purpose and does not take any special action other than to write the command and data to the chip.

Input parameters:

|           |          |                                           |
| --------- | -------- | ----------------------------------------- |
| DAData    | unsigned | 16-bit value in straight binary 0000-FFFF |
| DACommand | int      | 8-bit value in straight binary 00-FF      |

This function operates as follows:

Set page = 1

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

Write DAData to registers 0 and 1

Write DACommand byte to register 2

Set page = 0

End

### **BYTE SATURNDAUpdate(BoardInfo\* bi) ;**

This function is used to update the D/A when it is set for simultaneous mode (DASIM = 1) and the programmer is not using the DAConvertScan function. In this case the programmer is using DAConvert multiple times to write channel data individually. At the end of all these functions, the update command is needed to update all channels at once.

Input parameters:

None&#x20;

Function steps:

Set page = 1

Read DASIM bit (register 5 bit 0)

If DASIM = 0 then exit (simultaneous update mode is not in effect so DASIMUP command will have no effect)

Wait for DABUSY = 0 in register 7

Return timeout error if DABUSY does not return to 0 within the specified time limit

Write 0x80 to register 6 // DASIMUP command

Set page = 0

Exit

### **BYTE SATURNDARead(BoardInfo\* bi, int Chip, int Register, unsigned\* Value);**

This function enables the readback of internal registers in the AD5755 D/A converter. To implement the STATREAD function, read register 24.

Input parameters:

|          |          |                                                                              |
| -------- | -------- | ---------------------------------------------------------------------------- |
| Chip     | int      | Must be 0 // maintain consistency with RMM1616 function format               |
| Register | int      | 0-26; Selects which DAC register to read back; see AD5755 datasheet Table 28 |
| Value    | unsigned | 16-bit return value in straight binary 0000-FFFF                             |

![](broken-reference)

This function operates as follows:

Set page = 1

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

Write 0xAA55 to registers 0-1 // this is for debugging purposes only, the value has no effect on the operation

Write 0x80 + Register to register 2

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

Write 0xE000 to registers 0-1 // no op command when combined with MSB below

Write 0x1C to register 2

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

// Data is clocked into registers 0-1 during the transmission of the NOP command.

Read registers 0 and 1 to obtain LSB and MSB of DAC register value

Build 16-bit register value from MSB and LSB

Store register value in Value

Set page = 0

Exit

The following functions SetOffset, SetGain, and SetClearCode are identical except for the Command values written to the D/A chip.

### **BYTE SATURNSetOffset(BoardInfo\* bi, int Channel, unsigned Offset);**

This function programs a DAC channel’s offset (C) register. This is used during the calibration process

Input parameters:

|         |          |                                             |
| ------- | -------- | ------------------------------------------- |
| Channel | int      | 0-3                                         |
| Offset  | unsigned | 16-bit offset value; default value = 0x8000 |

This function operates as follows:

Set page = 1

Write Offset to registers 0-1

Command = 0x10 + Channel

Write Command to register 2

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

Set page = 0

Exit

### **BYTE SATURNSetGain(BoardInfo\* bi, int Channel, unsigned Gain);**

This function programs a DAC channel’s gain (M) register. This is used during the calibration process.

Input parameters:

|         |          |                                             |
| ------- | -------- | ------------------------------------------- |
| Channel | int      | 0-3                                         |
| Gain    | unsigned | 16-bit offset value; default value = 0xFFFF |

This function operates as follows:

Set page = 1

Write Gain to registers 0-1

Command = 0x08 + Channel

Write Command to register 2

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

Set page = 0

Exit

### **BYTE SATURNSetClearCode(BoardInfo\* bi, int Channel, unsigned ClearCode);**

This function programs a DAC channel’s clear code register. The clear code is the value that the channel will reset to when the chip is reset. The channel can be individually programmed to reset or not reset to the clear code with SATURNDASetSettings().

Input parameters:

|           |          |                                            |
| --------- | -------- | ------------------------------------------ |
| Channel   | int      | 0-3                                        |
| ClearCode | unsigned | 16-bit reset value; default value = 0x0000 |

This function operates as follows:

Set page = 1

Write Gain to registers 0-1

Command = 0x18 + Channel

Write Command to register 2

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

Set page = 0

Exit

### **BYTE SATURNSetSlew(BoardInfo\* bi, int Channel, int Enable, int SlewClock, int SlewStep);**

This function enables or disables slew rate control on an analog output channel. If enabled the slew rate is set with a combination of an increment (SlewStep) and an update rate (SlewClock). If slew rate is enabled, the slew operation may be monitored by checking the Ramp Active bit in the status register using the SATURNDARead() function.

Input parameters:

|           |     |                                                                             |
| --------- | --- | --------------------------------------------------------------------------- |
| Channel   | int | 0-3                                                                         |
| Enable    | int | 0 = disable slew rate control on this channel, 1 = enable slew rate control |
| SlewClock | int | if Enable = 1, this value is used to program the update rate; range 0-15    |
| SlewStep  | int | if Enable = 1, this value is used to program the increment; range 0-7       |

This function operates as follows:

Set page = 1

If Enable = 0 then:

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

Write 0x0000 to registers 0-1 // set SREN bit to 0 to disable slew rate function

Command = 0x1C  + Channel

Write Command to register 2

If Enable = 1 then:

Wait for DABUSY = 0

Return timeout error if DABUSY does not return to 0 within the specified time limit

Data = 0x1000 + SlewClock << 3 + SlewStep // set SREN bit to 1 to enable slew rate function

&#x20;               Write Data to registers 0-1

Command = 0x1C  + Channel

Write Command to register 2

Set page = 0

Exit

![](broken-reference)
