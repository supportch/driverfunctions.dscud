# DSCDIOINT

Structure containing interrupt-based Digital I/O settings. These settings determine the behavior of the interrupt-based D/A sampling operation. Please refer to the D/A interrupt description for complete explanation of interrupt behavior resulting from the various settings in this structure.

### Structure Definition

```c
typedef struct
{

    void* IntFunc;
    BOOL Enable ;
    BOOL Polarity;
    BOOL Intclr;

} DSCDIOINT;
```

### Structure Members

| Name     | Description                                                                                                                    | Applicable Boards |
| -------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| IntFunc  | pointer to user function to run when interrupts occur                                                                          | Helix,Zeta        |
| Enable   | 8 bit data to enable edge detection on DIO port B; 1 = enable, 0 = disable                                                     | Helix,Zeta        |
| Polarity | 8 bit data to select the active edge for interrupt generation;1 = rising, 0 = falling                                          | Helix,Zeta        |
| Intclr   | 1 = interrupt handler should clear interrupt clear registers; 0 = interrupt handler should not clear interrupt clear registers | Helix,Zeta        |
