# DSCADSCAN

### Structure Definition

```c
typedef struct {

    BYTE low_channel;
    BYTE high_channel;
    DSCSAMPLE* sample_values;
    BYTE gain;

} DSCADSCAN;
```

### Structure Members

| Name           | Description                                                                                                              | Applicable Boards                                                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| low\_channel   | The starting channel in the scan range on which to perform A/D conversions                                               | Diamond-MM-16-AT, Diamond-MM-32X-AT, Diamond-MM-16RP-AT, Diamond-MM-32DX-AT, Diamond-MM-AT, Helios                                     |
| high\_channel  | The ending channel in the scan range on which to perform A/D conversions; must be greater than or equal to low\_channel. | Diamond-MM-16-AT, Diamond-MM-32X-AT, Diamond-MM-16RP-AT, Diamond-MM-32DX-AT, Diamond-MM-AT, Helios                                     |
| sample\_values | Pointer to a buffer to hold the results of the A/D conversions                                                           | DS-MPE-DAQ0804, Zeta, Diamond-MM-16-AT, Diamond-MM-32X-AT, Diamond-MM-16RP-AT, Helix, Diamond-MM-32DX-AT, Aries, Diamond-MM-AT, Helios |
| gain           | Gain setting for A/D conversions; valid settings are GAIN\_1, GAIN\_2, GAIN\_4, or GAIN\_8                               | Diamond-MM-16-AT, Diamond-MM-16RP-AT, Diamond-MM-32DX-AT, Diamond-MM-32X-AT, Diamond-MM-AT, Helios                                     |
