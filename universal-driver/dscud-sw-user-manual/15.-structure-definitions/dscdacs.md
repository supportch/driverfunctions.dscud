# DSCDACS

Structure containing D/A conversion scan settings. This structure is used when performing analog output on several channels simultaneously. One array is filled with data for each channel, and a second array is filled with flags indicating which channels to change. The unselected channels are unchanged.

### Structure Definition

```c
typedef struct {

    BOOL channel_enable[16];
    DSCDACODE* output_codes;
    DSCDACODE DACode[4];
    
} DSCDACS;
```

### Structure Members

| Name                 | Description                                                                                                                                           | Applicable Boards                                                                                                                    |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| channel\_enable\[16] | Input Array of flags that selects which analog output channels to change. Select TRUE for each location (0-15) for which you want to output new data. | Aries,Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-32DX-AT, Diamond-MM-32X-AT,Diamond-MM-AT,Helix,DS-MPE-DAQ0804,Ruby-MM-1616,Zeta |
| output\_codes        | Input Array of output codes to send to the corresponding selected channels in channel\_enable\[]. Locations to use are 0-15.                          | Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-32DX-AT, Diamond-MM-32X-AT,Diamond-MM-AT,Ruby-MM-1616                                 |
| DACode\[4]           | Input Array of output codes to send to the corresponding selected channels in channel\_enable\[]. Locations to use are 0-3.                           | Aries,Helix,DS-MPE-DAQ0804,Zeta                                                                                                      |
