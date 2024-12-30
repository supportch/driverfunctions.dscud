# dsc9513PulseWidthModulation

```c
BYTE dsc9513PulseWidthModulation(DSCB board, DSCQMMPWM* pwm);
```

This function generates an output signal on the selected counter of GPIO-MM-11 or GPIO-MM-12 to the selected frequency with the selected duty cycle. The duty cycle is defined as the percent of time that the output is high. A 50% duty cycle represents a square wave (equal high and low periods), while a duty cycle of 0% means always low and a duty cycle of 100% means always high. The range for duty cycle is 0 to 99.99 in steps of .01. a duty cycle of 100% is not possible with this function.

The function takes as inputs the desired counter, output frequency, and duty cycle. It returns status information indicating the selected input frequency, the resulting load and hold register values, and a flag indicating whether the function has reached either duty cycle limit.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name      | Description                                              |
| --------- | -------------------------------------------------------- |
| DSCB      | The handle of the board to operate on                    |
| DSCQMMPWM | Structure containing configuration data for the function |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
