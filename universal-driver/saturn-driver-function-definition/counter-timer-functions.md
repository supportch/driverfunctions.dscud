# Counter/Timer Functions

### **BYTE SATURNCounterSetRate(BoardInfo\* bi, SATURNCOUNTER \*Ctr);**

This function programs a counter for timer mode with down counting and continuous operation (reload enabled). The output may be used for waveform generator control, interrupt generation, or for a general programmable-frequency output pulse train. The output may also be enabled on a DIO pin. The counter is started immediately. This function is a simplified version of CounterConfig() optimized for the most popular application of rate generator.

Input parameters:

|                |       |                                                                                  |
| -------------- | ----- | -------------------------------------------------------------------------------- |
| CtrNo          | int   | Counter number, 0-7                                                              |
| Rate           | float | Desired output rate, Hz                                                          |
| CtrOutEn       | int   | 1 = enable output onto corresponding I/O pin; 0 = disable output                 |
| CtrOutPol      | int   | 1 = positive output pulse; 0 = negative output pulse; only valid if CtrOutEn = 1 |
| CtrOutWidth    | int   | 0 = 1 clock; 1 = 10 clocks; 2 = 100 clocks; 3 = 1000 clocks                      |

This function performs as follows:

Set page = 3

If Rate >= 5 then Clock = 50MHz else Clock = 1MHz

Calculate Divisor = Clock / Rate

Write Divisor to registers 0-3

Write CtrNo to register 4

Command byte = 11110000 (reset counter)

Write command byte to register 5

Command byte = 00010000 (load data)

Write command byte to register 5

Command byte = 00100000 (set count down direction)

Write command byte to register 5

Command byte = 01100000 + clock setting (2 for 50MHz or 3 for 1MHz) (set clock source option)

Write command byte to register 5

Command byte = 00110000 (disable external gate)

Write command byte to register 5

Command byte = 10000000 + CtrOutEn \* 2 + CtrOutPol (enable/disable counter output and polarity)

Write command byte to register 5

Command byte = 10010000 + Outwidth (Output pulse width)

Write command byte to register 5

Command byte = 01110001 (enable auto-reload)

Write command byte to register 5

Command byte = 01000001 (enable counting)

Write command byte to register 5

Exit

### **BYTE SATURNCounterConfig(BoardInfo\* bi, SATURNCOUNTER \*Ctr);**

This function programs a counter for up or down counting and starts the counter running. A DIO pin may be selected as the input source. If a DIO pin is not selected as the input, and the counter is counting in down mode, the output may be enabled on the DIO pin. Using a DIO pin for input or output causes the FPGA to automatically set the DIO pin direction as needed.

Input parameters:

|               |               |                                                                                                                                               |
| ------------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Ctrno         | int           | Counter number, 0-7                                                                                                                           |
| CtrData       | unsigned long | Initial load data, 32-bit straight binary                                                                                                     |
| CtrClk        | int           | Clock source: 0 = external input, 2 = 50MHz, 3 = 1MHz                                                                                         |
| CtrCountDir   | int           | 0 = down counting, 1 = up  counting                                                                                                           |
| CtrReload     | int           | 0 = one-shot counting, 1 = auto-reload (repetitive counting, only works in count down mode)                                                   |
| CtrOutEn      | int           | 1 = enable output onto corresponding I/O pin; 0 = disable output                                                                              |
| CtrOutPol     | int           | 1 = output pulses high, 0 = output pulses low; only used if CtrOutEn = 1                                                                      |
| CtrOutWidth   | int           | 0 = 1 clock; 1 = 10 clocks; 2 = 100 clocks; 3 = 1000 clocks; only valid if internal clock is selected, otherwise output pulse is 1 clock wide |

This function performs as follows:

Set page = 3

Write data to registers 0-3

Write CtrNo to register 4

Command byte = 11110000 (reset counter)

Write command byte to register 5

Command byte = 00010000 (load data)

Write command byte to register 5

Command byte = 00100000 + CtrCountDir (set count up or down direction)

Write command byte to register 5

Command byte = 00110000 (disable external gate; no function in this board but will have a function in other boards)

Write command byte to register 5

Command byte = 10000000 (disable counter output)

Write command byte to register 5

Command byte = 01100000 + CtrClk (set clock source)

Write command byte to register 5

Command byte = 01110000 + CtrReload (enable/disable auto-reload)

Write command byte to register 5

// output enabled only if internal clock selected and count direction is down

If CtrOutEn = 1 and CtrClk = 2 or 3 and CtrCountDir = 0 then:

Command byte = 10000000 + CtrOutEn <<1 + CtrOutPol (select output enable and polarity)

Write command byte to register 5

Command byte = 10010000 + CtrOutWidth

Write command byte to register 5

Command byte = 01000001 (enable counting)

Write command byte to register 5

Exit
