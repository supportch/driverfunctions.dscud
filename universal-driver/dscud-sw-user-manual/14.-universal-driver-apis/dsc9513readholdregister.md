# dsc9513ReadHoldRegister

```c
BYTE dsc9513ReadHoldRegister(DSCB board, BYTE counter, WORD* value)
```

This function returns the 16-bit data in the selected counter's hold register. The counter data must first be latched by a Save or Save and Disarm command using dsc9513CounterControl() or dsc9513SingleCounterControl().

{% tabs %}
{% tab title=" Input Parameters" %}
| Name    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| DSCB    | The handle of the board to operate on                        |
| Counter | Counter no., 1-10 for GPIO-MM-11 and GPIO-MM-21              |
| Value   | 16-bit value from the counter's hold register, range 0-65535 |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
