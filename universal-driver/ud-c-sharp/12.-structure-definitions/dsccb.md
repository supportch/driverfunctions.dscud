# DSCCB

Structure containing hardware settings for the current board. Some elements are unique to particular boards.

## Structure Definition

```csharp
public struct DSCCB
    {
        public byte boardtype;
        public short boardnum;
        public ushort base_address;  
        public byte int_level;
        public byte DAC_Config;
        public int clock_freq;      
        public byte int_level1;
        public byte int_level2;
        public byte int_level3;
        public ushort fpga;
        public int FPGAIDMajor;   
        public int FPGAIDMinor;  
        public int FPGARev;       
        public int BoardIDMajor;  
        public int BoardIDMinor;  
        public int BoardRev;     

    }
```

## Structure Members

| Name          | Description                                                                                                                                                                                                                                                                               | Applicable Boards  |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| boardtype     | The board type constant; automatically filled by dscInitBoard;                                                                                                                                                                                                                            | Diamond-MM-16RP-AT |
| boardnum      | The handle to the board; automatically filled in by dscInitBoard                                                                                                                                                                                                                          | Diamond-MM-16RP-AT |
| base\_address | Base address of the board; refer to the board's user manual for valid base address settings                                                                                                                                                                                               | Diamond-MM-16RP-AT |
| int\_level    | Interrupt level of the board; used for boards with only one IRQ.                                                                                                                                                                                                                          | Diamond-MM-16RP-AT |
| DAC\_Config   | Resolution of the DAC to use in the code. If this flag is set to 0, the driver will always use the DAC as a 12 bit DAC - This helps for backward compatibility. When set to 1, 16 bit DAC will be used. This is only used by the DMM32DX board.For all other boards this field is ignored | NA                 |
| clock\_freq   | Counter maximium frequency                                                                                                                                                                                                                                                                | Diamond-MM-16RP-AT |
| int\_level1   | Interrupt level 1                                                                                                                                                                                                                                                                         | NA                 |
| int\_level2   | Interrupt level 2                                                                                                                                                                                                                                                                         | NA                 |
| int\_level3   | Interrupt level 3                                                                                                                                                                                                                                                                         | NA                 |
| fpga          | FPGA ID                                                                                                                                                                                                                                                                                   | Diamond-MM-16RP-AT |
| FPGAIDMajor   | FPGA ID Major                                                                                                                                                                                                                                                                             | NA                 |
| FPGAIDMinor   | FPGA ID Minor                                                                                                                                                                                                                                                                             | NA                 |
| FPGARev       | FPGA revision                                                                                                                                                                                                                                                                             | NA                 |
| BoardIDMajor  | Board ID Major                                                                                                                                                                                                                                                                            | NA                 |
| BoardIDMinor  | Board ID Minor                                                                                                                                                                                                                                                                            | NA                 |
| BoardRev      | Board revision                                                                                                                                                                                                                                                                            | NA                 |
