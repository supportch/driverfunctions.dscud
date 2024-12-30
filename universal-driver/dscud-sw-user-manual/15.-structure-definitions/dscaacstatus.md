# DSCAACSTATUS

Structure containing auto auto-calibration parameters for function dscAACGetStatus().

### Structure Definition

```c
typedef struct {

    BOOL pic_present;
    BOOL pic_busy;
    BOOL aac_hold;
    BOOL aac_error;
    BOOL aac_active;

} DSCAACSTATUS;
```

### Structure Members

| Name         | Description                                                   | Applicable Boards                     |
| ------------ | ------------------------------------------------------------- | ------------------------------------- |
| pic\_present | TRUE if PIC device is present, FALSE otherwise                | Diamond-MM-32X-AT, Diamond-MM-32DX-AT |
| pic\_busy    | TRUE if PIC device is busy with an operation, FALSE otherwise | Diamond-MM-32X-AT, Diamond-MM-32DX-AT |
| aac\_hold    | TRUE if AAC Hold-Off is enabled, FALSE otherwise              | Diamond-MM-32X-AT, Diamond-MM-32DX-AT |
| aac\_error   | TRUE if the last AAC command has failed, FALSE otherwise      | Diamond-MM-32X-AT, Diamond-MM-32DX-AT |
| aac\_active  | TRUE if the AAC routing is currently running, FALSE otherwise | Diamond-MM-32X-AT, Diamond-MM-32DX-AT |
