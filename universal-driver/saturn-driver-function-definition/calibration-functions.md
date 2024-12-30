# Calibration Functions

### **BYTE SATURNSetCalMux(BoardInfo\* bi, SATURNCALMUX\* Calmux);**

This function enables/disables the Calmux and configures the circuit for the desired signal polarity and input channel.

Input parameters:

|          |     |                        |
| -------- | --- | ---------------------- |
| Enable   | int | 0=disable, 1=enable    |
| Polarity | int | 0=positive, 1=negative |
| Channel  | int | 0-7                    |

This function operates as follows:

Set page = 5

If Enable = 0 then:

Write 0x00 to register 7

Set page = 0

Exit

Command = 0x02 | polarity (Set CALMUX bit and CALPOL bit)

Write command to register 7

Set page = 0

Chreg = Channel \* 0x10 + Channel (set high and low channels of input mux to desired channel)

Write chreg to register 2 (channel configuration register)

Sample ADWAIT until it is 0 (read register 3 bit 6)

Return Timeout error if ADWAIT does not return to 0 within the specified time limit

Set page = 0

Exit

### **BYTE SATURNADAutoCal(BoardInfo\* bi, SATURNADCAL\* Params);**

This function calibrates the A/D circuit for the specified range or for all ranges. It can also set the boot range to any selected input range.

Input parameters:

|                 |          |                                                                                                                                                                                                                         |
| --------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Range           | int      | 0-7 for single range or -1 for all ranges                                                                                                                                                                               |
| BootSet         | int      | 0 = don’t set boot range, 1 = set boot range                                                                                                                                                                            |
| BootRange       | int      |  0-7 for desired range to set as the boot range                                                                                                                                                                         |
| OffsetErrors    | float \* | Array of offset error values (low end of scale) resulting from calibration procedure. Any range that is calibrated will have a non-zero value. Any range that is not calibrated will have its tolerance value set to 0. |
| FullScaleErrors | float \* | Array of full-scale error values resulting from calibration procedure. Any range that is calibrated will have a non-zero value. Any range that is not calibrated will have its tolerance value set to 0.                |
| Express         | int      | 0 = run full calibration procedure, 1 = enable express mode                                                                                                                                                             |
| Tolerance       | float    | 0 = use driver default error tolerance, nonzero means use given tolerance                                                                                                                                               |
| Result          | int      | 0 = failure, 1 = success                                                                                                                                                                                                |

See separate document for A/D calibration procedure.

If range = 0-7 then calibrate only the selected range, else calibrate ranges 0-7 in succession.

Store offset and full-scale errors in arrays

After calibration is complete:

If BootSet = 1 then store TrimDAC values from range selected by BootRange to EEPROM addresses 0-3

If all errors are within selected tolerance then Result = 1 (success) else Result = 0 (failure)

Exit

### **BYTE SATURNADCalVerify(BoardInfo\* bi, SATURNADCAL\* Params);**

This function enables the quick verification of A/D calibration settings by reading the calibration voltages and reporting the error between the readings and the target values.

Input parameters:

|                 |          |                                                                                                                                                                                                        |
| --------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Range           | int      | 0-7 for single range or -1 for all ranges                                                                                                                                                              |
| OffsetErrors    | float \* | Array of offset error values (low end of scale) resulting from verification. Any range that is verified will have a non-zero value. Any range that is not verified will have its error value set to 0. |
| FullScaleErrors | float \* | Array of full-scale error values resulting from verification. Any range that is verified will have a non-zero value. Any range that is not calibrated will have its error value set to 0.              |
| Tolerance       | float    | 0 = use driver default error tolerance, nonzero means use given tolerance                                                                                                                              |
| Result          | int      | 0 = failure, 1 = success                                                                                                                                                                               |

This function operates as follows:

Obtain Target value from EEPROM for selected range (CMn where n = A/D range number)

Convert Target voltage to A/D counts

Set calmux to correct channel for low end of range

Take N A/D samples and compute average; do not round

Calculate error = average – Target; do not round

Store error in OffsetErrors array

Set calmux to correct channel for high end of range

Take N A/D samples and compute average; do not round

Calculate error = average – Target; do not round

Store error in FullScaleErrors array

If all ranges selected (Range = -1), repeat for all ranges

If all errors are less than global tolerance CoarseTol, report Result = 1, else Result = 0

Exit

### **BYTE SATURNSetTrimDAC(BoardInfo\* bi, int TrimDAC, int Value);**

This function programs the selected TrimDAC with the selected data. SATURN has 12 trimDACs numbered 0-11. The data is 8 bits unsigned ranging from 0 to 255.

Input parameters:

|           |     |       |
| --------- | --- | ----- |
| TrimDAC   | int | 0-11  |
| Value     | int | 0-255 |

This function operates as follows:

Set page = 5

Store TrimDAC number in register 0

Store Value in register 4

Write command 0x08 to register 6 (Set TDACEN = 1)

Sample TDBUSY until it is 0 (read register 7 bit 6)

Return Timeout error if TDBUSY does not return to 0 within the specified time limit

Set page = 0

Exit

### **BYTE SATURNGetReferenceVoltages(BoardInfo\* bi, float\* Refs);**

This function retrieves the complete set of reference voltages stored in the EEPROM and stores them in an array. The valid values are in locations 0-3 and 8-11 of the EEPROM.

Output parameters:

|      |          |                                                    |
| ---- | -------- | -------------------------------------------------- |
| Refs | float \* | Pointer to array to receive the reference voltages |

This function operates as follows:

Set page = 5

Write EEPROM unlock code 0xA5 to register 8

Write EEPROM unlock code 0x24 to register 8

Read 3-byte CM values 0, 1, 2, 3, 8, 9, 10, and 11 from EEPROM

Convert CM values to voltages using the conversion formula

Store voltages in array

Set array values 4, 5, 6, 7, 12, 13, 14, and 15 to 0

Set page = 0

Exit

### **BYTE SATURNSetReferenceVoltages(BoardInfo\* bi, float\* Refs);**

This function stores the complete set of given reference voltages in the EEPROM. The valid values are in locations 0-3 and 8-11 of the EEPROM.

Input parameters:

|       |          |                                              |
| ----- | -------- | -------------------------------------------- |
| Refs  | float \* | Pointer to array with the reference voltages |

This function operates as follows:

Set page = 5

Write EEPROM unlock code 0xA5 to register 8

Write EEPROM unlock code 0x24 to register 8

Convert values in array locations 0, 1, 2, 3, 8, 9, 10, and 11 to 3-byte CM values using the conversion formula

Store CM values in EEPROM

Set page = 0

Exit

Conversion from EEPROM 3-byte value CMn\[2-0] to voltage (n = 0-3 or 8-11):

&#x20;               V = (CMn\[2] & 0x7E) /2 + ((CMn\[2] & 1) \* 2^16 + CMn\[1] \* 2^8 + CMn\[0]) / 1,000,000

&#x20;               if (sign == 1) V = -V

### **BYTE SaturnSerialConfig(BoardInfo\* bi, DSCSERIALCONFIG \*serialconfig)**

This function will change the serial protocol and store into EEPROM as per customer request

**Input Parameters**:

DSCSERIALCONFIG \*serialconfig

* Int Protocol – which is the array, can set the protocol mode in Protocol\[0] variable as following below

0    - RS232,

1 - RS422,

1    - RS485

* Int Action –

0\.  Set Serial port mode.

1\.  Set Serial port mode and update EEPROM

2\.  Read EEPROM

* BYTE\* eeprom\_data - Curent EEPROM setting for serial port registers.
* int Slewrate - To select Slew rate.

This function work’s as follows,

Setpage – 8

Write the data into Reg 0 and store the result into EEPROM

If user select then we will read the data from EEPROM.

Setpage - 0

### **BYTE SaturnAutoRTS(**&#x42;oardInf&#x6F;**\* bi, DSCAutoRTS \*AutoRTS)**

This function will enable or disable RTS for RS422 & RS485

**Input parameter**:

DSCAutoRTS **\*AutoRTS**

* Unsigned int DataLength – Data length will be 5-8 and start & stop bits.
* BYTE Enable – 1 enable or 0 disable the RTS.
* BYTE Port – which port we are going to use (0 or 1).
* BYTE Pol – polarity of the port to high or low pulse

(If RTSPOL = 0, the RTSOUT pin is normally low, and the pulse will be high. If RTSPOL = 1, the RTSOUT pin is normally high, and the pulse will be low. In Auto RTS mode, the RTS input signal for a port is ignored).

* Double baudrate – Baudrate which are using for COM1 & COM2 (1200 - 256000).

This function work’s as follows

Setpage – 8

Calculating the time by this equation(datalength/baudrates) and copy into FPGA registers offset 2(LSB) & 3(MSB).

Also will copy RTS\_Enable & Polarity values into FPGA register offset-3(MSB).

Setpage – 0
