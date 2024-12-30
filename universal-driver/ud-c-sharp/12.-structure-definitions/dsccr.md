# DSCCR

Structure containing information on all counters. This is used for functions operating on 82C54 counters.

## Structure Definition

```csharp
    public struct DSCCR
    {
        public byte control_code;   /* [INPUT] Counter command byte.- Refer Board manual for specifics */

        public byte counter_number; /* [INPUT] Counter number to which the settings are being applied. */

        public uint counter_data;   /* [INPUT] Data to set the counter to */

        public DSCCS counter0;      /* [OUTPUT] Counter 0 data read */

        public DSCCS counter1;      /* [OUTPUT] Counter 1 data read */

        public DSCCS counter2;      /* [OUTPUT] Counter 2 data read */

        public byte control_bit;    /* [INPUT] Used in conjunction with control_code */

        /// DSC_DIO_PORTS_MAX=8
        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 8, ArraySubType = System.Runtime.InteropServices.UnmanagedType.Struct)]
        public DSCCS[] counter;       /* [OUTPUT] Counter 2 data read */

        public int CtrClock;        //Clock source, must be 2 or 3 (see FPGA specification for usage)

        public int CtrOutEn;        //1= enable output onto corresponding I/O pin; 0 = disable output

        public int CtrOutPol;       //1= output pulses high, 0 = output pulses low; only used if CtrOutEn = 1

        public int CtrCountDir;     /*0 = down counting, 1 = up  counting*/

        public int CtrReload;       /*0 = one-shot counting, 1 = auto-reload (repetitive counting, only works in count down mode)*/

        public float Rate;          // Desired output rate, Hz

        public int ctrOutWidth;     // 0-3   0 = 1 clocks, 1 = 10 clocks, 2 = 100 clocks, 3 = 1000 clocks , only used if  CtrOutEn = 1 and CtrClock = 2 or 3

        public int CtrCmd;          /*Counter command, 0-15 (see FPGA specification for available commands)*/

        public int CtrCmdData;      /*Auxiliary data for counter command, 0-3 (see FPGA specification for usage)*/

        public float ActRate;       //Actual rate resulting from the closest divisor available for the desired rate

        public int Start;           //0 = don’t start counter after configuration; 1 = start counter after configuration

        public int GateEn;          //0 = no external gate; 1 = external gate enabled in RMM1616
        
    }
```

## Structure Members

| Name            | Description                                                                   | Applicable Boards  |
| --------------- | ----------------------------------------------------------------------------- | ------------------ |
| control\_code   | Control code to write to or read from the control word register               | Diamond-MM-16RP-AT |
| counter\_number | Selected counter, 0-2                                                         | Diamond-MM-16RP-AT |
| counter\_data   | Counter divisor value, 0-65535                                                | Diamond-MM-16RP-AT |
| counter0        | Status and data read from counter 0                                           | Diamond-MM-16RP-AT |
| counter1        | Status and data read from counter 1                                           | Diamond-MM-16RP-AT |
| counter2        | Status and data read from counter 2                                           | Diamond-MM-16RP-AT |
| control\_bit    | Used in conjunction with control\_code                                        | NA                 |
| counter\[]      | Counter 2 data read                                                           | NA                 |
| CtrClock        | Clock source                                                                  | NA                 |
| CtrOutEn        | Enable and disable output onto corresponding I/O pin                          | NA                 |
| CtrOutPol       | Output pulses high or low only used if CtrOutEn = 1                           | NA                 |
| CtrCountDir     | Setting counter direction                                                     | NA                 |
| CtrReload       | Setting auto reload                                                           | NA                 |
| Rate            | Desired output rate, Hz                                                       | NA                 |
| ctrOutWidth     | Counter output width in terms of clock                                        | NA                 |
| CtrCmd          | Counter commands                                                              | NA                 |
| CtrCmdData      | Auxiliary data for counter command                                            | NA                 |
| ActRate         | Actual rate resulting from the closest divisor available for the desired rate | NA                 |
| Start           | To start the counter                                                          | NA                 |
| GateEn          | To enable external gate in RMM1616                                            | NA                 |
