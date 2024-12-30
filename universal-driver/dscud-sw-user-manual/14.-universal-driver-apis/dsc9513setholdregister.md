# dsc9513SetHoldRegister

```c
BYTE dsc9513SetHoldRegister(DSCB board, BYTE counter, WORD value)
```

This function is identical to dsc9513SetLoadRegister() except the data is loaded into the selected counter's Hold register instead of the Load register. In some operating modes of the 9513 counter chip, the counter alternates between the Load register and the Hold register when reloading. This feature can be used to generate square waves with variable duty cycles (PWM signals) by loading different values in the Load and Hold registers. See the descriptions of the counter modes in the 9513 datasheet for more detail on the uses of this register.
