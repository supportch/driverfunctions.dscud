# DSCPWM

Structure containing pulse width modulation parameters for DscPWMFunction().

### Structure Definition

```c
typedef struct {

    DFLOAT output_freq;
    FLOAT duty_cycle;
    BYTE polarity;
    BYTE pwm_circuit;
    BOOL output_enab;
    BYTE run;
    BOOL Divisor;

} DSCPWM;
```

### Structure Members

| Name         | Description                                                                                                                       | Applicable Boards                                                    |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| output\_freq | Output frequency of the PWM signal (i.e. frequency of subsequent duty cycles.)                                                    | DS-MPE-GPIO,Ruby-MM-1616,Zeta,P104-GPIO96,Aries,Helix,DS-MPE-DAQ0804 |
| duty\_cycle  | Percentage of time that the signal will be in the active state. Valid duty cycles range from 0.0 to 100.0.                        | DS-MPE-GPIO,Ruby-MM-1616,Zeta,P104-GPIO96,Aries,Helix,DS-MPE-DAQ0804 |
| polarity     | Determines the active state of the PWM signal (for boards that support this.) 0 = high, 1 = low                                   | DS-MPE-GPIO,Ruby-MM-1616,Zeta,P104-GPIO96,Aries,Helix,DS-MPE-DAQ0804 |
| pwm\_circuit | Which PWM circuit this function should configure. Depending on the board this will represent either physical or logical counters. | DS-MPE-GPIO,Ruby-MM-1616,Zeta,P104-GPIO96,Aries,Helix,DS-MPE-DAQ0804 |
| output\_enab | Enable signal output. 1 = enable, 0 = disable                                                                                     | DS-MPE-GPIO,Ruby-MM-1616,Zeta,P104-GPIO96,Aries,Helix,DS-MPE-DAQ0804 |
| run          | To initiate and run the PWM                                                                                                       | DS-MPE-GPIO,Ruby-MM-1616,Zeta,P104-GPIO96,Aries,Helix,DS-MPE-DAQ0804 |
| Divisor      | 24-bit value for use with period and duty cycle commands                                                                          | DS-MPE-GPIO,Ruby-MM-1616,Zeta,P104-GPIO96,Aries,Helix,DS-MPE-DAQ0804 |
