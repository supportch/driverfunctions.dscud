# A/D functions

### **BYTE SATURNADSetSettings(BoardInfo\* bi, SATURNADSETTINGS\* settings);**

This function configures the A/D input range, channel register, and scan settings. It can optionally recall the A/D calibration settings for the selected input range.

#### Input parameters:

|              |      |                                                                         |
| ------------ | ---- | ----------------------------------------------------------------------- |
| Gain         | int  | 0-3: 0 = 1, 1 = 2, 2 = 4, 3 = 8                                         |
| Polarity     | int  |  0-1; 0 = bipolar, 1 = unipolar                                         |
| Sedi         | int  | 0-1; 0 = single-ended, 1 = differential                                 |
| Lowch        | int  | low channel, 0-15                                                       |
| Highch       | int  | high channel, 0-15                                                      |
| LoadCal      | bool | True/False                                                              |
| ScanEnable   | int  | 0 = disable, 1 = enable                                                 |
| ScanInterval | int  | 0 = 10us, 1 = 5us, 2 = 8us, 3 = programmable                            |
| ProgInt      | int  | 100-255, used if Interval = 3 (minimum limit is not enforced in driver) |

This function operates as follows:

Set page = 0

Build register 2 value (input channels) from Lowch and Highch parameters

Write value to register 2

Calculate Scansize = Highch – Lowch + 1

Write Sedi to register 3

Build register 4 value (input range) from Gain and Polarity parameters

Write value to register 4

Build register 6 value (scan settings) from ScanEnable and ScanInterval

Write value to register 6

If ScanInterval = 3 then write ProgInt value to register 7

If LoadCal = True:

&#x20;       Recall A/D calibration values for selected input range from EEPROM (4 values)

&#x20;       Write calibration values to TrimDACs

&#x20;       On each write to TrimDAC:

&#x20;              Wait for TDBUSY = 0

&#x20;              Return Timeout error if TDBUSY does not return to 0 within the specified time limit

Wait for ADWAIT = 0 (register 3 bit 6)

Return Timeout error if ADWAIT does not return to 0 within the specified time limit

Exit

### **BYTE SATURNADSetRange(BoardInfo\* bi, SATURNADSETTINGS\* settings);**

This function configures the A/D input range. All other settings remain as is.

Input parameters:

|          |     |                                         |
| -------- | --- | --------------------------------------- |
| Gain     | int | 0-3: 0 = 1, 1 = 2, 2 = 4, 3 = 8         |
| Polarity | int | 0-1; 0 = bipolar, 1 = unipolar          |
| Sedi     | int | 0-1; 0 = single-ended, 1 = differential |

This function operates as follows:

Set page = 0

Build register 4 value (input range) from Gain, Polarity, and Sedi parameters

Write value to register 4

Wait for ADWAIT = 0 (register 3 bit 6)

Return Timeout error if ADWAIT does not return to 0 within the specified time limit

Exit

### **BYTE SATURNADSetChannel(BoardInfo\* bi, SATURNADSETTINGS\* settings);**

This function configures the A/D input channel range. All other settings remain as is.

Input parameters:

|        |     |                    |
| ------ | --- | ------------------ |
| Lowch  | int | low channel, 0-15  |
| Highch | int | High channel, 0-15 |

This function operates as follows:

Set page = 0

Build register 2 value (input channels) from Lowch and Highch parameters

Write value to register 2

Calculate Scansize = Highch – Lowch + 1 // wrap around 15 to 0 is allowed

Wait for ADWAIT = 0 (register 3 bit 6)

Return Timeout error if ADWAIT does not return to 0 within the specified time limit

Exit

### **BYTE SATURNADSetScan(BoardInfo\* bi, SATURNADSETTINGS\* settings);**

This function configures the A/D logic for scan operation. It does not configure any other settings on the board.

Input parameters:

|              |     |                                              |
| ------------ | --- | -------------------------------------------- |
| ScanEnable   | int | 0 = disable, 1 = enable                      |
| ScanInterval | int | 0 = 10us, 1 = 5us, 2 = 8us, 3 = programmable |
| ProgInt      | int | 125-255, used if Interval = 3                |

This function operates as follows:

Set page = 0

Build register 6 value (scan settings) from ScanEnable and ScanInterval

Write value to register 6

If ScanInterval = 3 then write ProgInt value to register 7

Exit

### **BYTE SATURNADSetClock(BoardInfo\* bi, BYTE ADclk);**

This function configures the clock source for A/D conversions.

Input parameters:

|       |     |                                                                                                                               |
| ----- | --- | ----------------------------------------------------------------------------------------------------------------------------- |
| ADClk | int | 0-3: 0 = software command (ADSample or ADScan function), 1 = falling edge on DIO0, 2 = counter 0 output, 3 = counter 1 output |

This function operates as follows:

Set page = 0

value = ADclk

// ADCLKEN is only set when the interrupt function is started.

Write value to register 5

Exit

### **BYTE SATURNADStartClock(BoardInfo\* bi);**

This function enables the clock source for A/D conversions.

Input parameters:

None



This function operates as follows:

Set page = 0

Read register 5

Set ADCLKEN bit

Write new value to register 5

Exit

### **BYTE SATURNADStopClock(BoardInfo\* bi);**

This function disables the clock source for A/D conversions.

Input parameters:

None

&#x20;

This function operates as follows:

Set page = 0

Read register 5

Clear ADCLKEN bit

Write new value to register 5

Exit

### **BYTE SATURNADRead(BoardInfo\* bi, unsigned\* Sample);**

This function reads one A/D sample out of the FIFO if the FIFO is not empty. If the FIFO is empty, it returns an error FIFO\_EMPTY. The purpose of this function is to enable reading A/D data acquired with counter/timer or external triggering without having to use interrupts.

&#x20;

This function operates as follows:

Set page = 4

Read FIFO depth in registers 4 and 5

If depth = 0, return error FIFO\_EMPTY and Sample is set to 0

Set page = 0

Read A/D data in registers 0 and 1

Convert data to 16-bit value and store in Sample

Exit

### **BYTE SATURNADSample(BoardInfo\* bi, unsigned\* Sample);**

This function executes one A/D conversion using the current board settings. It does not perform any configuration of the board or the FPGA but rather uses the current settings. It assumes that the board is configured for sample mode, not scan mode.

Output parameters:

|        |          |                                                                                                                                                                        |
| ------ | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sample | unsigned | Return value, 16 bits; may be interpreted as unsigned integer 0 - 65535 or signed integer -32768 – 32767 depending on the A/D configuration and software expectations. |

This function operates as follows:

Set page = 0

Write 0x80 to register 0 to start conversion (ADSTART = 1)

Monitor ADBUSY (register 3 bit 7)

Return Timeout error if ADBUSY does not return to 0 within the specified time limit

Read A/D value from registers 0 and 1 and store in Sample

Exit

### **BYTE SATURNADScan(BoardInfo\* bi unsigned\* Sample);**

This function executes one A/D scan (sample on all channels between Lowch and Highch). It uses all existing A/D settings on the board. It assumes that the board is configured for scan mode, not sample mode.

Output parameters:

<table><thead><tr><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Sample</td><td>unsigned</td><td>pointer to array of return values, 16 bits; may be interpreted as unsigned integer 0 - 65535 or signed integer -32768 – 32767 depending on the A/D configuration and software expectations. The size of this array must be equal to or greater than the maximum number of channels available on the board (16).</td></tr></tbody></table>

This function operates as follows:

Set page = 0

Write 0x80 to register 0 to start scan (ADSTART = 1)

Monitor ADBUSY (register 3 bit 7)

Return Timeout error if ADBUSY does not return to 0 within the specified time limit

When ADBUSY = 0, an entire scan of samples will be stored in the A/D FIFO.

Read all A/D values from registers 0 and 1 and store in array; the number of samples to read is equal to Scansize. This will have been calculated previously during SATURNADSetSettings() or SATURNADSetChannel().

Exit

### **BYTE SATURNADInt(BoardInfo\* bi, SATURNADINT\* SATURNadint);**

This function enables A/D interrupt operation using the current analog input settings. It configures the FIFO and the clock source on the board.

Input parameters (part of SATURNADINT data structure):

|                 |             |                                                                                                                                                                                                                |
| --------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| FIFOEnable      | int         | 0 = disable; interrupt occurs after each sample / scan; 1 = enable; interrupt occurs on FIFO threshold flag                                                                                                    |
| FIFOThreshold   | int         | 0-2048, indicates level at which FIFO will generate an interrupt if FIFOEnable = 1                                                                                                                             |
| Cycle           | int         | 0 = one shot operation, interrupts will stop when the selected no. of samples / scans are acquired; 1 = continuous operation until terminated                                                                  |
| ADClk           | int         | 0-3 selects A/D clock source                                                                                                                                                                                   |
| NumConversions  | int         | if Cycle = 0 this is the number of samples / scans to acquire; if Cycle = 1 this is the size of the circular buffer in samples / scans                                                                         |
| ADBuffer        | unsigned \* | pointer to A/D buffer to hold the samples; the buffer must be greater than or equal to NumConversions x 1 if scan is disabled or NumConversions x Scansize if scan is enabled (Scansize is Highch – Lowch + 1) |

**Procedure:**

Disable A/D clock

Reset A/D FIFO

Configure FIFO settings

Install interrupt routine

Set up buffer in kernel

Configure A/D clock source

If counter/timer is used, reset counter so it starts at beginning

Enable A/D interrupts

&#x20;

This function operates as follows:

Set page = 0

Write 0 to register 5 to stop A/D clock

Set page = 4

Write 0x80 to register 13 to reset FIFO

If FIFOEnable = 1 then:

&#x20;               Write FIFO threshold to register 0 and 1

&#x20;               Write 0x01 to register 12 to enable FIFO

Clear SampleCount variable

Store Cycle parameter

Install pointer to A/D interrupt routine

Configure A/D buffer in kernel according to NumConversions and ScanEnable register bit

Store interrupt parameters Cycle and NumConversions for use by interrupt routine

If internal counter/timer 0 or 1 is selected as clock source:

&#x20;               Stop counter/timer using SATURNCounterFunction(): CtrNo = 0 or 1, CtrCmd = 0100, CCD0 = 0

&#x20;               Reset counter/timer using SATURNCounterFunction(): CtrNo = 0 or 1, CtrCmd = 0000

Set page = 7

Read register 0

Set ADINTEN, retain other bits

Write value to register 0

Set page = 0

If internal counter/timer 0 or 1 is selected as clock source:

&#x20;               Start counter/timer using SATURNCounterFunction(): CtrNo = 0 or 1, CtrCmd = 0100, CCD0 = 1

Write ADclk + ADCLKEN = 1 to register 5 // Enable AD clock for A/D conversions only after all other settings are in place

Set page = 0

Exit

### **SATURNADIntHandler();**

This function processes A/D interrupts. It is called by the operating system interrupt handler in Universal Driver when a hardware interrupt occurs on the selected level for the board. It will also run a user interrupt function if user interrupts have been configured. This function is internal to the driver and is never called directly by the user.

Procedure:

Check ADINT status, if 0 then exit: Page 7 register 1 bit 0

If UserInterrupt = 1 and UserInterruptMode = 1 (before) then run user interrupt routine

Read A/D data from board (sample, scan, or FIFO threshold qty)

Store A/D data in buffer mod buffer size; interrupt routine must manage the buffer pointer

Increment SampleCount by 1, ScanSize, or FIFO Threshold

Clear A/D interrupt request on board

&#x20;               Set page = 7

&#x20;               Write 0x01 to register 1

If SampleCount >= NumConversions, then:

&#x20;               If Cycle = 0 stop interrupts

&#x20;               If Cycle = 1 nothing needs to be done

If UserInterrupt = 1 and UserInterruptMode = 2 (after) then run user interrupt routine

Exit

### **BYTE SATURNADIntStatus(BoardInfo\* bi, SATURNADINTSTATUS\* intstatus);**

This function returns the interrupt routine status including, running / not running, number of conversions completed, cycle mode, FIFO status, and FIFO flags.

Output parameters (part of SATURNADINTSTATUS data structure):

|                    |     |                                                  |
| ------------------ | --- | ------------------------------------------------ |
| OpStatus           | int | 0 = not running, 1 = running                     |
| NumConversions     | int | Number of conversions since interrupts started   |
| Cycle              | int | 0 = one-shot operation, 1 = continuous operation |
| FIFODepth          | int | Current FIFO depth pointer                       |
| UF, OF, FF, TF, EF | int | FIFO flags                                       |

**This function operates as follows:**

Set page = 7

OpStatus = ADINTEN, register 0 bit 0

Set page = 4

FIFODepth = depth value in registers 4 and 5

Flags = values in register 13; Each return value is either 1 or 0

NumConversions = SampleCount managed by interrupt handler

Cycle = Cycle parameter stored by SATURNADInt()

Set page = 0

Exit

### **BYTE SATURNADIntPause(BoardInfo\* bi);**

This function pauses A/D interrupts by turning off the interrupt enable and stopping the A/D  clock. This holds the A/D channel counter and FIFO at their current positions. Interrupts may be resumed from the point at which they were stopped with the Resume function.

Input parameters:

None



This function operates as follows:

Set page = 0

Read ADCLK1-0 in register 5

Clear ADCLKEN bit

Rewrite register 5

If counter/timer 0 or 1 is selected, then:

&#x20;               Stop counter/timer using SATURNCounterFunction(): CtrNo = 0 or 1, CtrCmd = 0100, CCD0 = 0

&#x20;               Clear counter/timer using SATURNCounterFunction(): CtrNo = 0 or 1, CtrCmd = 0000

Set page = 7

Set ADINTEN = 0, retain other bits in register 0

Set page = 0

Exit

### **BYTE SATURNADIntResume(BoardInfo\* bi);**

This function resumes A/D interrupts from the point at which they were paused. This function cannot be used to initiate interrupt operations because it does not set up the board or the driver to handle interrupts.&#x20;

Input parameters:

None



This function operates as follows:

Set page = 7

Set ADINTEN = 1, retain other bits in register 0

Set page = 0

Read ADCLK1-0 in register 5

Set ADCLKEN bit = 1

Rewrite register 5

If counter/timer 0 or 1 is selected, then:

&#x20;               Start counter/timer using SATURNCounterFunction(): CtrNo = 0 or 1, CtrCmd = 0100, CCD0 = 1

Set page = 0

Exit

### **BYTE SATURNADIntCancel(BoardInfo\* bi);**

