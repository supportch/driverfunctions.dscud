# dscDIOOutputInt

```c
BYTE dscDIOOutputInt(DSCB board,DSCDIOINT *dscdioint);
```

This function installs a pointer to a user function that runs when digital interrupts occur. Interrupts are driven by the edge detection circuit.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name      | Description                                                                                                                                                                                                                                                                                                                                                                             |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DSCB      | The handle of the board to operate on                                                                                                                                                                                                                                                                                                                                                   |
| DSCDIOINT | Enable int 8 bit data to enable edge detection on DIO port B; enable=1, disable =0; IntFunc void\* pointer to user function to run when interrupts occur Polarity int 8 bit data to select the active edge for interrupt generation;1 = rising, 0 = falling Int clr int 1 = interrupt handler clear interrupt clear registers; 0= interrupt handler not clear interrupt clear registers |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
