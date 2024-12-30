# DSCADCALPARAMS

Structure containing A/D auto-calibration settings. Used by dscADAutocal().

### Structure Definition

```c
typedef struct { 

    BYTE adrange; 
    BYTE boot_adrange; 
    FLOAT ad_offset; 
    FLOAT ad_gain; 
    DFLOAT target_values[AD_MAX_REFS_VOLT];    
    } DSCADCALPARAMS;
```

### Structure Members

| Name                                 | Description                                                                                             | Applicable Boards                                                                                  |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| adrange                              | A/D range to calibrate; if adrange = 255, then all A/D ranges will be calibrated                        | Diamond-MM-16-AT, Diamond-MM-32X-AT, Diamond-MM-16RP-AT, Diamond-MM-32DX-AT, Diamond-MM-AT, Helios |
| boot\_adrange                        | A/D range whose calibration settings will be loaded from the EEPROM when the board is first powered on. | Diamond-MM-16-AT, Diamond-MM-32X-AT, Diamond-MM-16RP-AT, Diamond-MM-32DX-AT, Diamond-MM-AT, Helios |
| ad\_offset                           | The maximum offset error in A/D LSBs resulting from the autocalibration process                         | Diamond-MM-16-AT, Diamond-MM-32X-AT, Diamond-MM-16RP-AT, Diamond-MM-32DX-AT, Diamond-MM-AT, Helios |
| ad\_gain                             | The maximum gain error in A/D LSBs resulting from the autocalibration process                           | Diamond-MM-16-AT, Diamond-MM-32X-AT, Diamond-MM-16RP-AT, Diamond-MM-32DX-AT, Diamond-MM-AT, Helios |
| target\_values\[AD\_MAX\_REFS\_VOLT] | OUTPUT: Target values read from EEPROM                                                                  | Diamond-MM-16-AT, Diamond-MM-32X-AT, Diamond-MM-16RP-AT, Diamond-MM-32DX-AT, Diamond-MM-AT, Helios |
