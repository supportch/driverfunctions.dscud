# DSCSPECIALFUNC

Structure containing information on all special functions.&#x20;

### Structure Definition

```c
typedef struct {

    BYTE cmd;
    BOOL *Data;
    BOOL Config;

} DSCSPECIALFUNC;
```

### Structure Members

| Name   | Description                                                                                                                                                                                                                                                                                    | Applicable Boards            |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| cmd    | Command provided from the user                                                                                                                                                                                                                                                                 | Aries                        |
| Data   | To read the data from the device                                                                                                                                                                                                                                                               | Aries                        |
| Config | <p>Pull Up/Down configuration value</p><p>Values : 0 - 3</p><p>0 - All DIO lines Pull down</p><p>1 - Group 1 DIO lines pull up and </p><p>     Group 2 DIO lines Pull down</p><p>2 - Group 1 DIO lines pull down </p><p>     and Group 2 DIO lines Pull up</p><p>3 - All DIO lines Pull up</p> | DS-MPE-GPIO, DS-MPE-DAQ0804. |
