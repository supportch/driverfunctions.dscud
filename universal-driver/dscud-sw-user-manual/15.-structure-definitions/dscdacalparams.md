# DSCDACALPARAMS

Structure containing parameters used in D/A auto-calibration.

### Structure Definition

```c
typedef struct { 
    
    BOOL fixed;
    DFLOAT darange; 
    FLOAT offset; 
    FLOAT gain; 
    FLOAT cal_point; 
    BOOL ch0pol, ch0prog, ch0ext; 
    BOOL ch1pol, ch1prog, ch1ext; 
    FLOAT ref; 
    
    } DSCDACALPARAMS;
```

### Structure Members

| Name       | Description                                                                                                                                                                              | Applicable Boards                                                                      |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| fixed      | fixed=0 means programmable darange; fixed=1 then  darange is fixed.                                                                                                                      |                                                                                        |
| darange    | Desired full-scale voltage for custom D/A range setting, in volts. Used only when in Programmable mode, otherwise ignored. Range is anywhere between 1.0 and 10.0 in increments of .001. | Diamond-MM-16-AT,Diamond-MM-32X-AT,Diamond-MM-16RP-AT,Diamond-MM-32DX-AT,Diamond-MM-AT |
| offset     | Error in D/A LSB counts at the mid-scale of the D/A range                                                                                                                                | Diamond-MM-16-AT,Diamond-MM-32X-AT,Diamond-MM-16RP-AT,Diamond-MM-32DX-AT,Diamond-MM-AT |
| gain       | Error in D/A LSB counts at the full-scale (high end) of the D/A range                                                                                                                    | Diamond-MM-16-AT,Diamond-MM-32X-AT,Diamond-MM-16RP-AT,Diamond-MM-32DX-AT,Diamond-MM-AT |
| cal\_point | Desired D/A point voltage for custom calibration setting, in volts. Range is anywhere in valid D/A range.                                                                                | Diamond-MM-32DX-AT                                                                     |

The following parameters are used only on Diamond-MM-AT. This board has independent D/A settings for each analog output channel. The parameters below correspond to the jumper settings on the board.

| Name             | Description                                                                        |
| ---------------- | ---------------------------------------------------------------------------------- |
| ch0pol, ch1pol   | Polarity setting for each D/A channel: 0 = bipolar, 1 = unipolar                   |
| ch0prog, ch1prog | Programmable setting for each D/A channel: 0 = fixed range, 1 = programmable range |
| ch0ext, ch1ext   | ch0ext, ch1ext                                                                     |
| ref              | For internal use only.                                                             |

The parameter darange\_calibrate is used for Helios board only. This parameter is used to perform DA calibration verification on the mode being verified. The valid modes are specified in the DA table. The valid values for this parameter are

| Value | Description           |
| ----- | --------------------- |
| 0     | ( 0 to 10V UNIPOLAR ) |
| 1     | ( 0 to 5V UNIPOLAR )  |
| 4     | (+/- 2.5V BIPOLAR)    |
| 5     | (+/- 5V BIPOLAR)      |
| 6     | (+/- 10V BIPOLAR)     |

