# Digital I/O Functions

### **BYTE SATURNDIOConfig(BoardInfo\* bi, int Port, int Config);**

This function sets the digital I/O port direction for the selected port.

Input parameters:

|        |     |                                              |
| ------ | --- | -------------------------------------------- |
| port   | int | 0-2 for port A, B, C                         |
| config | int | 8-bit configuration values for selected port |

This function operates as follows:

Set page = 2

Write configuration byte Config to base address + 8 + Port (8, 9 or 10)

Set page = 0

Exit

### **BYTE SATURNDIOConfigAll(BoardInfo\* bi, int\* Config);**

This function sets the digital I/O port directions for all ports at once.&#x20;

Input parameters:

<table><thead><tr><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Config                      </td><td>int *</td><td>pointer to 3 8-bit configuration values for ports A, B, C</td></tr></tbody></table>

This function operates as follows:

Set page = 2

Write 4 configuration values in Config array to base address + 8, 9 and 10

Set page = 0

Exit

### **BYTE SATURNDIOOutputByte(BoardInfo\* bi, int Port, byte Data);**

This function outputs the specified data to the specified port. The data is 8 bits for ports A , B and 6 bits for port C.

Input parameters:

<table><thead><tr><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Port</td><td>int</td><td>0=A, 1=B, 2=C</td></tr><tr><td>Data</td><td>int</td><td>6 or 8 bit value to write to the port; for port C only the lower 6 bits are used, the upper 2 are ignored by the FPGA</td></tr></tbody></table>

This function operates as follows:

Set page = 2

Write data to register 8 + port no.

Set page = 0

Exit

### **BYTE SATURNDIOInputByte(BoardInfo\* bi, int Port, byte\* Data);**

This function reads in the data from the specified port and returns it in the location specified by the pointer to data.

Input parameters:

|      |        |                                                |
| ---- | ------ | ---------------------------------------------- |
| Port | int    |  0 = A, 1 = B, 2 = C                           |
| Data | int \* | pointer to receive the data read from the port |

This function operates as follows:

Set page = 2

Read the register specified by Port

Store the value in the location specified by Data

Exit

### **BYTE SATURNDIOOutputBit(BoardInfo\* bi, int Port, int Bit, int Value);**

This function outputs a single bit to an output port. The other bits remain at their current values.

Input parameters:

|       |     |                                                                                 |
| ----- | --- | ------------------------------------------------------------------------------- |
| Port  | int | Port to write bit to: 0 = A, 1 = B, 2 = C                                       |
| Bit   | int | 0-7 indicates the bit position in the port (for port C the value should be 0-5) |
| Value | int | 0 or 1                                                                          |

This function operates as follows:

Set page = 2

Read the register specified by Port number (since port is in output mode this reads the output register value)

If Value = 0 then mask off selected bit and rewrite data

If Value = 1 then or in selected bit and rewrite data

Set page = 0

Exit

### **BYTE SATURNDIOInputBit(BoardInfo\* bi, int Port, int Bit, int\* Value);**

This function reads in the specified bit from the specified port and returns it in the location specified by the pointer to data.

Input parameters:

|       |        |                                                               |
| ----- | ------ | ------------------------------------------------------------- |
| Port  | int    | 0 = A, 1 = B, 2 = C                                           |
| Bit   | int    | 0-7 for ports A and B, 0-5 for port C                         |
| Value | int \* | pointer to receive the bit data; return data is always 0 or 1 |

This function operates as follows:

Set page = 2

Read the register specified by Port number

Mask off the selected bit and right shift into bit 0; return data is always 0 or 1

Store the value in the location specified by Value

Set page = 0

Exit
