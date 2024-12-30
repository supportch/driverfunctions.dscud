# ERRPARAMS

Structure containing error code information resulting from a Universal Driver function call. An error code is generated as the return value by each driver function.

### Structure Definition

```c
typedef struct {

    BYTE ErrCode;
    char* errstring;

} ERRPARAMS;
```

### Structure Members

| Name      | Description                                                       | Applicable Boards |
| --------- | ----------------------------------------------------------------- | ----------------- |
| ErrCode   | The error code representing the particular error                  | All boards        |
| errstring | The string description corresponding to the error code in ErrCode | All boards        |
