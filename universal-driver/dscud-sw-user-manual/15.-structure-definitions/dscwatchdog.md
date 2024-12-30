# DSCWATCHDOG

### Structure Definition

```c
typedef struct {
 
    WORD wd1; 
    BYTE wd2; 
    BYTE HardwareTriggerEnable; 
    BYTE EdgeSelection; 
    BYTE CountEarly ; 
    BYTE InterruptEnable; 
    Void (*IntFunc) (void *parameter); 
    
    } DSCWATCHDOG;
```

### Structure Members

| Name                  | Description                                                                                                                                                                                           | Applicable Boards |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| wd1                   | 16-bit timer value (runs at \~32KHz - max 2 seconds)                                                                                                                                                  | Aries             |
| wd2                   | 8-bit timer value (runs at \~32KHz - max 7.2ms)                                                                                                                                                       | Aries             |
| HardwareTriggerEnable | 0 = disable, 1 = enable                                                                                                                                                                               | Aries             |
| EdgeSelection         | if HardwareTriggerEnable = 1, then 0 = Raising edge 1 = falling edge                                                                                                                                  | Aries             |
| CountEarly            | 0 = disable, 1 = enable i.e. DIO C4 goes high when counter A = 1 instead of 0 , This enables C4 to be externally wired to C5 to cause an automatic repetitive retrigger when WDIEN = 1 and WDEDGE = 0 | Aries             |
| InterruptEnable       | 1= when counter A reaches 0 an interrupt will occur, 0=interrupt will not occur                                                                                                                       | Aries             |
| IntFunc               | pointer to user function to run when interrupts occur                                                                                                                                                 | Aries             |
