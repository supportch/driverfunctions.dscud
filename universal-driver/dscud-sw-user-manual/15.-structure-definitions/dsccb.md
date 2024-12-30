# DSCCB

Structure containing hardware settings for the current board. Some elements are unique to particular boards.

### Structure Definition

```c
typedef struct { 

    BYTE boardtype; 
    DSCB boardnum; 
    WORD base_address; 
    BYTE int_level;  
    BYTE DAC_Config; // ONLY USED FOR DMM32DX 
    LONG clock_freq
    BYTE int_level1
    BYTE int_level2
    BYTE int_level3
    WORD fpga
    BOOL FPGAIDMajor
    BOOL FPGAIDMinor
    BOOL FPGARev
    BOOL BoardIDMajor
    BOOL BoardIDMinor
    BOOL BoardRev
    
    } DSCCB;
```

### Structure Members

| Name          | Description                                                                                                                                                                                                                                                                               | Applicable Boards                                                                                                                                                      |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| boardtype     | The board type constant; automatically filled by dscInitBoard;                                                                                                                                                                                                                            | Diamond-MM-16-AT, Diamond-MM-16RP-AT, Diamond-MM-AT,P104-GPIO96, Helix, DS-MPE-DAQ0804, DS-MPE-GPIO, Ruby-MM-1616                                                      |
| boardnum      | The handle to the board; automatically filled in by dscInitBoard                                                                                                                                                                                                                          | All boards                                                                                                                                                             |
| base\_address | Base address of the board; refer to the board's user manual for valid base address settings                                                                                                                                                                                               | All boards                                                                                                                                                             |
| int\_level    | Interrupt level of the board; used for boards with only one IRQ.                                                                                                                                                                                                                          | Diamond-MM-16-AT, Diamond-MM-AT, P104-GPIO96, P104-GPIO96, Helix, Aries, Diamond-MM-32DX-AT, Diamond-MM-32X-AT, GPIO-MM-11, GPIO-MM-21, Onyx-MM, Zeta                  |
| DAC\_Config   | Resolution of the DAC to use in the code. If this flag is set to 0, the driver will always use the DAC as a 12 bit DAC - This helps for backward compatibility. When set to 1, 16 bit DAC will be used. This is only used by the DMM32DX board.For all other boards this field is ignored | Diamond-MM-32DX-AT                                                                                                                                                     |
| clock\_freq   | Counter maximium frequency                                                                                                                                                                                                                                                                | Diamond-MM-16-AT, Diamond-MM-16RP-AT, Diamond-MM-AT, Diamond-MM-32DX-AT, Diamond-MM-32X-AT, Onyx-MM                                                                    |
| int\_level1   | Interrupt level 1                                                                                                                                                                                                                                                                         | GPIO-MM-11, GPIO-MM-21, Onyx-MM                                                                                                                                        |
| int\_level2   | Interrupt level 2                                                                                                                                                                                                                                                                         | GPIO-MM-11, GPIO-MM-21, Onyx-MM                                                                                                                                        |
| int\_level3   | Interrupt level 3                                                                                                                                                                                                                                                                         | Onyx-MM                                                                                                                                                                |
| fpga          | FPGA ID                                                                                                                                                                                                                                                                                   | Diamond-MM-AT, P104-GPIO96, Helix, DS-MPE-DAQ0804, DS-MPE-GPIO, Ruby-MM-1616, Aries, Diamond-MM-32DX-AT, Diamond-MM-32X-AT, Zeta, Diamond-MM-16-AT, Diamond-MM-16RP-AT |
| FPGAIDMajor   | FPGA ID Major                                                                                                                                                                                                                                                                             | Aries, Zeta                                                                                                                                                            |
| FPGAIDMinor   | FPGA ID Minor                                                                                                                                                                                                                                                                             | Aries, Zeta                                                                                                                                                            |
| FPGARev       | FPGA revision                                                                                                                                                                                                                                                                             | Aries, Zeta                                                                                                                                                            |
| BoardIDMajor  | Board ID Major                                                                                                                                                                                                                                                                            | Aries, Zeta                                                                                                                                                            |
| BoardIDMinor  | Board ID Minor                                                                                                                                                                                                                                                                            | Aries, Zeta                                                                                                                                                            |
| BoardRev      | Board revision                                                                                                                                                                                                                                                                            | Aries, Zeta                                                                                                                                                            |
