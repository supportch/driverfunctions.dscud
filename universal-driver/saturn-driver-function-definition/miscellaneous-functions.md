# Miscellaneous Functions

### **BYTE SATURNInitBoard(DSCCB\* dsccb, SATURNINIT \*Init);**

Input parameters (part of SATURNINIT data structure):

|             |     |                                                        |
| ----------- | --- | ------------------------------------------------------ |
| Address     | int | Base address assigned to board in PCI I/O memory space |
| IRQ         | int | IRQ number assigned to board                           |

Output parameters (part of SATURNINIT data structure):

|              |     |                                                  |
| ------------ | --- | ------------------------------------------------ |
| FPGAIFMajor  | int | FPGA ID major value                              |
| FPGAIDMinor  | int | FPGA ID minor value                              |
| FPGARev      | int | FPGA Revision                                    |
| BoardIDMajor | int | Board ID major value                             |
| BoardIDMinor | int | Board ID minor value                             |
| BoardRev     | int | Board Revision                                   |
| ADChannels   | int | A/D chip presence / number of channels indicator |
| DAChannels   | int | D/A chip presence / number of channels indicator |

Sequence of operations:

1\.       Pass in board base address and IRQ setting.

2\.       Verify board’s presence by read/write to a register and by reading the board ID registers.

3\.       Read number of A/D and D/A channels from page 15 registers 0 (A/D) and 2 (D/A). Register 0 valid values are 0x00 and 0x10; register 2 valid values are 0x00 and 0x04.

4\.       If both registers read 0, then the DAQ circuit is not present and the driver returns an error code.

5\.       Initialize D/A chip based on no. of channels (0,4) using procedure below.

6\.       Return FPGA ID, FPGA revision, board ID, board revision, and number of A/D and D/A channels.

D/A chip initialization procedure:

1\.       Perform chip reset with command 1C8555

2\.       (Wait 200us) // not specified in datasheet, this is for safety and can be removed if unnecessary

3\.       Program main control registers with command 1C2000

4\.       Program clear code registers on all channels with MSB = 0x18 + channel no. 0,1,2,3; CSB = 00; LSB = 00 (4 commands)

5\.       Program DC/DC control register  with command 1C6077

6\.       Write to all DAC control registers on all DAC chips to set 0-5V range with OUTEN = 0:

MSB = 0x1C + channel no. 0,1,2,3, CSB = 41; LSB = 10 (4 commands)

7\.       Wait for DABUSY = 0

8\.       Write 0x0000 to all DAC registers (4 commands): MSB=00 + channel no, CSB=00, LSB=00

9\.       Wait 200us

10\.   Write to all DAC control registers to set 0-5V range with OUTEN = 1:

MSB = 0x1C + channel no. 0,1,2,3; CSB = 41; LSB = 50  (4 commands)

11\.   Wait for DABUSY = 0

Interrupt number setting:

Set page no to 7

Write interrupt number to offset 3

Set page no to 0

### **BYTE SATURNFreeBoard(DSCB board);**

This function stops any active interrupt processes and frees the interrupt resources assigned to a board. It then decrements the driver’s count of the number of active I/O boards under its control. Next it calls DSCFreeBoardSubSys() remove the board handle from the driver’s list of boards. Finally this function can execute any specific code needed for this board.

Input parameters:

None

This function is identical for all I/O boards (except for the board-specific termination code), so this function can be copied from an existing board in the driver.

### **BYTE SATURNFIFOStatus(BoardInfo\* bi, SATURNFIFO\* SATURNfifo);**

Output parameters:

|            |     |                                                                                                                                                                 |
| ---------- | --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Threshold  | int | Current FIFO programmed threshold                                                                                                                               |
| Depth      | int | Current FIFO depth pointer                                                                                                                                      |
| Enable     | int | 0 = FIFO is not currently enabled, 1 = FIFO is currently enabled                                                                                                |
| UF         | int | 0 = no underflow, 1 = FIFO underflow (attempt to read was made when FIFO was empty)                                                                             |
| OF         | int | 0 = no overflow, 1 = FIFO overflow (attempt to write into FIFO when FIFO was full)                                                                              |
| FF         | int | 0 = FIFO not full, 1 = FIFO is full                                                                                                                             |
| TF         | int | 0 = number of A/D samples in FIFO is less than the programmed threshold, 1 = number of A/D samples in FIFO is equal to or greater than the programmed threshold |
| EF         | int | 0 = FIFO has unread data in it, 1 = FIFO is empty                                                                                                               |

This function returns the current FIFO depth and status flags in the parameter array. The flags are in page 4 register 13.

This function operates as follows:\
Set page = 4

Read registers 0-1 and store value in Threshold

Read registers 4-5 and store value in Depth

Read register 12 FIFOEN bit and store in Enable

Read register 13 (FIFO flags) and store 1/0 values in UF, OF, FF, TF, and EF

Set page = 0

Exit

### **BYTE SATURNEEPROMRead(BoardInfo\* bi, int Address, int\* Data);**

This function reads the 8-bit data from the data acquisition EEPROM at the given address.

Input parameters:

|         |     |                                 |
| ------- | --- | ------------------------------- |
| Address | int | EEPROM address, 0-511           |
| Data    | int | EEPROM data read from the EEPRO |

This function operates as follows:

Set page = 5

Sample EEBUSY until it is 0 (read register 7 bit 7)

Return Timeout error if EEBUSY does not return to 0 within the specified time limit

Write address to registers 0/1

Write command 0xC0 to address 6 to initiate the read operation (EEEN = 1 and EERW = 1)

Sample EEBUSY until it is 0 (read register 7 bit 7)

Return Timeout error if EEBUSY does not return to 0 within the specified time limit

Read data from register 4 and store in Data

Set page = 0

Exit

### **BYTE SATURNEEPROMWrite(BoardInfo\* bi, int Address, int Data);**

This function writes the given 8-bit data to the data acquisition EEPROM at the given address. It does not allow access to the protected area that holds the backup calibration information.

Input parameters:

|         |     |                                    |
| ------- | --- | ---------------------------------- |
| Address | int | EEPROM address, 0-127 or 256-5     |
| Data    | int | EEPROM data to write to the EEPROM |

This function operates as follows:

If Address in range 128-255 then error: invalid address

Set page = 5

Sample EEBUSY until it is 0 (read register 7 bit 7)

Return Timeout error if EEBUSY does not return to 0 within the specified time limit

Write unlock code 0xA5 to register 8

Write unlock code 0x24 to register 8

Write address to registers 0/1

Write data to register 4

Write command 0x80 to address 6 to initiate the write operation (EEEN = 1 and EERW = 0)

Set page = 0

Exit

### **BYTE SATURNEEPROMWriteX(BoardInfo\* bi, int Address, int Data);**

This function writes the given 8-bit data to the data acquisition EEPROM at the given address. It allows access to all addresses including the protected area with factory calibration backup. This function is not published in the user API.

Input parameters:

|         |     |                                    |
| ------- | --- | ---------------------------------- |
| Address | int | EEPROM address 0-511               |
| Data    | int | EEPROM data to write to the EEPROM |

This function operates as follows:

Set page = 5

Sample EEBUSY until it is 0 (read register 7 bit 7)

Return Timeout error if EEBUSY does not return to 0 within the specified time limit

If address < 128 or address > 255:

Write 0xA5 to register 8

Write 0x24 to register 8

If address >= 128 and address <= 255:

Write 0x4D to register 9

Write 0x0A to register 9

Write address to registers 0/1

Write data to register 4

Write command 0x80 to address 6 to initiate the write operation (EEEN = 1 and EERW = 0)

Set page = 0

Exit

### **BYTE SATURNDAMonitor(BoardInfo\* bi, float\* Status)**

This function reads the voltage values of D/A output channels 1-3. These signals are routed into the calmux circuit.

Input parameters:

|        |          |                                                            |
| ------ | -------- | ---------------------------------------------------------- |
| Status | float \* | Array of float values to store return data; array size = 3 |

This function operates as follows:

Set page = 5

Write 0x02 to register 7 (CALMUX = 1 and CALPOL = 0)

Set page = 0

Set A/D range to +/-10V using driver function

Perform A/D conversions on channels 5, 6, and 7 using driver function

Store results in Status array

Set page = 0

Exit

