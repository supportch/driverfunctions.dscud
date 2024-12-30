# DSCCR

Structure containing information on all counters. This is used for functions operating on 82C54 counters (all boards except Quartz-MM).

### Structure Definition

```c
typedef struct {

    BYTE control_code;
    BYTE counter_number;
    DWORD counter_data;
    DSCCS counter0;
    DSCCS counter1;
    DSCCS counter2;
    BOOL CtrClock;
    BOOL CtrOutEn;
    BOOL CtrOutPol;
    BOOL CtrCountDir;
    BOOL CtrReload;
    FLOAT Rate;
    BOOL ctrOutWidth;
    BOOL CtrCmd;
    BOOL CtrCmdData;
    FLOAT ActRate;
    BOOL Start;
    BOOL GateEn;
    
} DSCCR;
```

### Structure Members

| Name            | Description                                                                   | Applicable Boards                                                                                                                                                    |
| --------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| control\_code   | Control code to write to or read from the control word register               | Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-AT,Helix,Onyx-MM,Zeta,Diamond-MM-32DX-AT,Diamond-MM-32X-AT                                                            |
| counter\_number | Selected counter, 0-2                                                         | Ruby-MM-1616,Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-AT,Helix,Onyx-MM,Zeta,Diamond-MM-32DX-AT,Diamond-MM-32X-AT,Aries,P104-GPIO96,DS-MPE-DAQ0804,DS-MPE-GPIO  |
| counter\_data   | Counter divisor value, 0-65535                                                | Ruby-MM-1616,Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-AT,Onyx-MM ,Diamond-MM-32DX-AT,Diamond-MM-32X-AT,Aries,P104-GPIO96,Helix,DS-MPE-DAQ0804,DS-MPE-GPIO,Zeta |
| counter0        | Status and data read from counter 0                                           | Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-AT,Onyx-MM                                                                                                            |
| counter1        | Status and data read from counter 1                                           | Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-AT,Onyx-MM                                                                                                            |
| counter2        | Status and data read from counter 2                                           | Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-AT,Onyx-MM                                                                                                            |
| CtrClock        | Clock source                                                                  | Ruby-MM-1616,Aries,Helix,DS-MPE-DAQ0804,DS-MPE-GPIO,Zeta,P104-GPIO96                                                                                                 |
| CtrOutEn        | Enable and disable output onto corresponding I/O pin                          | Ruby-MM-1616,Aries,P104-GPIO96,DS-MPE-DAQ0804,DS-MPE-GPIO,Helix,DS-MPE-GPIO,Zeta                                                                                     |
| CtrOutPol       | Output pulses high or low only used if CtrOutEn = 1                           | Ruby-MM-1616,Aries,DS-MPE-DAQ0804,DS-MPE-GPIO,Helix,Zeta                                                                                                             |
| CtrCountDir     | Setting counter direction                                                     | Ruby-MM-1616,P104-GPIO96,Helix,DS-MPE-DAQ0804,Zeta,Aries,DS-MPE-GPIO                                                                                                 |
| CtrReload       | Setting auto reload                                                           | Ruby-MM-1616,Helix,DS-MPE-DAQ0804,DS-MPE-GPIO,Zeta,P104-GPIO96,Aries                                                                                                 |
| Rate            | Desired output rate, Hz                                                       | Aries,P104-GPIO96,DS-MPE-DAQ0804,DS-MPE-GPIO,Helix,Ruby-MM-1616,Zeta                                                                                                 |
| ctrOutWidth     | Counter output width in terms of clock                                        | Aries,DS-MPE-DAQ0804,DS-MPE-GPIO,Helix,Zeta                                                                                                                          |
| CtrCmd          | Counter commands                                                              | P104-GPIO96,Aries,Helix,Ruby-MM-1616,Zeta,DS-MPE-DAQ0804                                                                                                             |
| CtrCmdData      | Auxiliary data for counter command                                            | Aries,Helix,Ruby-MM-1616,Zeta,DS-MPE-DAQ0804,P104-GPIO96                                                                                                             |
| ActRate         | Actual rate resulting from the closest divisor available for the desired rate | Helix,Zeta                                                                                                                                                           |
| Start           | To start the counter                                                          | Helix,Zeta                                                                                                                                                           |
| GateEn          | To enable external gate in RMM1616                                            | Ruby-MM-1616                                                                                                                                                         |
