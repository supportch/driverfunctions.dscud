# Data Structures

The following data structures are used in the SATURN driver functions.

### **SATURNINIT**

|              |        |                                                          |
| ------------ | ------ | -------------------------------------------------------- |
| Address      | int    | Base address assigned to board in PCI I/O memory space   |
| IRQ          | int    | IRQ number assigned to board                             |
| FPGAIDMajor  | int    | FPGA ID major value                                      |
| FPGAIDMinor  | int    | FPGA ID minor value                                      |
| FPGARev      | int    | FPGA Revision                                            |
| BoardIDMajor | int    | Board ID major value                                     |
| BoardIDMinor | int    | Board ID minor value                                     |
| BoardRev     | int    | Board Revision                                           |
| SerNo        | char\* | Serial number string                                     |
| Date         | char\* | Date of last factory calibration in BCD format, YYYYMMDD |
| ADChannels   | int    | A/D chip presence / number of channels indicator         |
| DAChannels   | int    | D/A chip presence / number of channels indicator         |

### **SATURNADSETTINGS**

|                |     |                                                                           |
| -------------- | --- | ------------------------------------------------------------------------- |
| Gain           | int | 0-3: 0 = 1, 1 = 2, 2 = 4, 3 = 8                                           |
| Polarity       | int | 0-1; 0 = bipolar, 1 = unipolar                                            |
| Sedi           | int | 0-1; 0 = single-ended, 1 = differential                                   |
| Lowch          | int | Low channel, 0-15                                                         |
| Highch         | int | High channel, 0-15                                                        |
| LoadCalBool    | int | True/False; True = recall calibration settings after changing input range |
| ScanEnable     | int | 0 = disable, 1 = enable                                                   |
| ScanInterval   | int | 0 = 10us, 1 = 5us, 2 = 8us, 3 = programmable using ProgInt                |
| ProgInt        | int | 125-255, used if Interval = 3                                             |

### &#x20;**SATURNADINT**

|                |            |                                                                                                                                                                                                                |
| -------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| FIFOEnable     | int        | 0 = disable; interrupt occurs after each sample / scan; 1 = enable; interrupt occurs on FIFO threshold flag                                                                                                    |
| FIFOThreshold  | int        | 0-2048, indicates level at which FIFO will generate an interrupt if FIFOEnable = 1                                                                                                                             |
| Cycle          | int        | 0 = one shot operation, interrupts will stop when the selected no. of samples / scans are acquired; 1 = continuous operation until terminated                                                                  |
| ADClk          | int        | 0-3 selects A/D clock source                                                                                                                                                                                   |
| NumConversions | int        | if Cycle = 0 this is the number of samples / scans to acquire; if Cycle = 1 this is the size of the circular buffer in samples / scans                                                                         |
| ADBuffer       | sword \*   | pointer to A/D buffer to hold the samples; the buffer must be greater than or equal to NumConversions x 1 if scan is disabled or NumConversions x Scansize if scan is enabled (Scansize is Highch – Lowch + 1) |

### **SATURNADINTSTATUS**

<table><thead><tr><th width="210.33333333333331"></th><th></th><th></th></tr></thead><tbody><tr><td>OpStatus   </td><td>int</td><td>0 = Interrupts not running, 1 = Interrupts running</td></tr><tr><td>NumConversions</td><td>int</td><td>Number of conversions since interrupts started</td></tr><tr><td>BufferPtr   </td><td>int</td><td>Position in A/D storage buffer, used in continuous mode when buffer is being repetitively overwritten</td></tr><tr><td>Cycle  </td><td>int</td><td>0 = one-shot operation, 1 = continuous operation</td></tr><tr><td>FIFODepth   </td><td>int</td><td> Current FIFO depth pointer</td></tr><tr><td>UF</td><td>int</td><td>0 = no underflow, 1 = FIFO underflow (attempt to read was made when FIFO was empty)</td></tr><tr><td>OF</td><td>int</td><td>0 = no overflow, 1 = FIFO overflow (attempt to write into FIFO when FIFO was full)</td></tr><tr><td>FF</td><td>int</td><td>0 = FIFO not full, 1 = FIFO is full</td></tr><tr><td>TF</td><td>int</td><td>0 = number of A/D samples in FIFO is less than the programmed threshold, 1 = number of A/D samples in FIFO is equal to or greater than the programmed threshold</td></tr><tr><td>EF</td><td>int</td><td>0 = FIFO has unread data in it, 1 = FIFO is empty</td></tr></tbody></table>

### **SATURNFIFO**

|              |     |                                                                                                                                                                  |
| ------------ | --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Threshold    | int | Current FIFO programmed threshold                                                                                                                                |
| Depth        | int | Current FIFO depth pointer                                                                                                                                       |
| Enable       | int | 0 = FIFO is not currently enabled, 1 = FIFO is currently enabled                                                                                                 |
| UF           | int | 0 = no underflow, 1 = FIFO underflow (attempt to read was made when FIFO was empty)                                                                              |
| OF           | int | 0 = no overflow, 1 = FIFO overflow (attempt to write into FIFO when FIFO was full)                                                                               |
| FF           | int | 0 = FIFO not full, 1 = FIFO is full                                                                                                                              |
| TF           | int |  0 = number of A/D samples in FIFO is less than the programmed threshold, 1 = number of A/D samples in FIFO is equal to or greater than the programmed threshold |
| EF           | int | 0 = FIFO has unread data in it, 1 = FIFO is empty                                                                                                                |

### **SATURNCALMUX**

|          |     |                                                            |
| -------- | --- | ---------------------------------------------------------- |
| Enable   | int | 0 = disable, 1 = enable                                    |
| Polarity | int | 0 = use native positive value, 1 = enable inverter circuit |
| Channel  | int | 0-7 = selected channel number of calibration multiplexor   |

### **SATURNADCAL**

|                  |          |                                                                                                                                                                                                                         |
| ---------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Range            | int      | 0-7 for single range or -1 for all ranges                                                                                                                                                                               |
| BootSet          | int      | 0 = don’t set boot range, 1 = set boot range                                                                                                                                                                            |
| BootRange        | int      | 0-7 for desired range to set as the boot range                                                                                                                                                                          |
| OffsetErrors     | float \* | array of offset error values (low end of scale) resulting from calibration procedure. Any range that is calibrated will have a non-zero value. Any range that is not calibrated will have its tolerance value set to 0. |
| FullScaleErrors  | float \* | array of full-scale error values resulting from calibration procedure. Any range that is calibrated will have a non-zero value. Any range that is not calibrated will have its tolerance value set to 0.                |
| Express          | int      | 0 = run full calibration procedure, 1 = enable express mode                                                                                                                                                             |
| Tolerance        | float    | 0 = use driver default error tolerance, nonzero means use given tolerance                                                                                                                                               |
| Result           | int      | 0 = failure, 1 = success                                                                                                                                                                                                |

### **SATURNDASETTINGS**

|              |          |                                                                                 |
| ------------ | -------- | ------------------------------------------------------------------------------- |
| RangeA       |  int     | 0-3 to select full scale output ranges 10V, 5V, 2.5V, or 1.25V for channels 0-3 |
| RangeB       |  int     | 0-3 to select full scale output ranges 10V, 5V, 2.5V, or 1.25V for channels 4-7 |
| PolarityA    |  int     | 0 = bipolar (+/-nV), 1 = unipolar (0-nV) for channels 0-3                       |
| PolarityB    |  int     | 0 = bipolar (+/-nV), 1 = unipolar (0-nV) for channels 0-3                       |
| Mode         |  int     | 0 = binary (0 to 65535), 1 = 2s complement (-32768 to 32767) data format        |
| Simultaneous |  int     | 0 = single update mode, 1 = simultaneous update mode                            |
| LoadCalA     |  int     | True/False; True = recall calibration settings after changing input range       |
| LoadCalB     |  int     | True/False; True = recall calibration settings after changing input range       |

### **SATURNWAVEFORM**

|             |             |                                                                                                                                                                                                                                                                                                             |
| ----------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Waveform    | unsigned \* | pointer to array of 16-bit unsigned data; If multiple channels are being set up at the same time, the data must be previously interleaved by the program, i.e. ch. 0, ch. 1, ch. 2, ch. 0, ch. 1, ch. 2, …; the array size must be equal to Frames x Framesize; the array size must be no greater than 2048 |
| Frames      |  int        | total number of frames in the array                                                                                                                                                                                                                                                                         |
| Framesize   |  int        | no. of channels to be driven = frame size                                                                                                                                                                                                                                                                   |
| Channels    |  int  \*    | List of channels to be driven by the waveform generator; the number of values in this array must be equal to Framesize; channels can be in any sequence                                                                                                                                                     |
| Clock       |  int        | 0 = software increment; 1 = counter/timer 0 output; 2 = counter/timer 1 output; 3 = DIO pin D0                                                                                                                                                                                                              |
| Rate        |  int        | frame update rate, Hz (only used if Clock = 1 or 2)                                                                                                                                                                                                                                                         |
| Cycle       |  int        | 0 = one-shot operation; 1 = repetitive operation                                                                                                                                                                                                                                                            |

### **SATURNCOUNTER**

|               |               |                                                                                                              |
| ------------- | ------------- | ------------------------------------------------------------------------------------------------------------ |
| CtrNo         | int           |  Counter number, 0-7                                                                                         |
| CtrData       | unsigned long | Initial load data, 32-bit straight binary                                                                    |
| CtrClock      | int           | Clock source, must be 2 or 3                                                                                 |
| CtrOutEn      | int           | 1 = enable output onto corresponding I/O pin; 0 = disable output                                             |
| CtrOutPol     | int           | 1 = output pulses high, 0 = output pulses low; only used if CtrOutEn = 1                                     |
| CtrCountDir   | int           | 0 = down counting, 1 = up counting                                                                           |
| CtrReload     | int           | 0 = one-shot counting, 1 = auto-reload (repetitive counting, only works in count down mode)                  |
| CtrCmd        | int           | Counter command, 0-15 (see user manual for available commands)                                               |
| CtrCmdData    | int           | Auxiliary data for counter command, 0-3 (see user manual for usage)                                          |
| Rate          | float         | Desired output rate, Hz                                                                                      |
| CtrOutWidth   | int           | 0 = 1 clock, 1 = 10 clocks, 2 = 100 clocks, 3 = 1000 clocks; only used if CtrOutEn = 1 and CtrClock = 2 or 3 |

### **SATURNUSERINT**

|            |         |                                                                         |
| ---------- | ------- | ----------------------------------------------------------------------- |
| IntFunc    | void \* | pointer to user function to run when interrupts occur                   |
| Mode       | Int     | 0 = alone, 1 = before standard function, 2 = after standard function    |
| Source     | int     | 0 = counter/timer 2 output, 1 = digital input D1; used only if mode = 0 |
| Enable     | int     | 0 = disable interrupts, 1 = enable interrupts                           |

### **SATURNPWM**

|              |          |                                                                   |
| ------------ | -------- | ----------------------------------------------------------------- |
| Num          | int      | PWM number, 0-3                                                   |
| Rate         | float    | output frequency in Hz                                            |
| Duty         | float    |  initial duty cycle, 0-100                                        |
| Polarity     | int      | 0 = pulse high, 1 = pulse low                                     |
| OutputEnable | int      | 0 = disable output, 1 = enable output on DIO pin                  |
| Run          | int      | 0 = don\92t start PWM, 1 = start PWM                              |
| Command      | int      | 0-15 = PWM command                                                |
| CmdData      | int      | 0 or 1 for auxiliary PWM command data (used for certain commands) |
| Divisor      | int      | 24-bit value for use with period and duty cycle commands          |

