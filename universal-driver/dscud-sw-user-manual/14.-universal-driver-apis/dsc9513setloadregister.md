# Dsc9513SetLoadRegister

```c
BYTE dscQMMSetLoadRegister(DSCB board, BYTE counter, WORD value)
```

This function loads the supplied data into the specified counter's Load register. The Load register is used to specify a counter's initial value as well as to set the reload value when the counter reaches its terminal count during repetitive counting modes. The data is not actually loaded into the counter's count register until a Load or Load and Arm command is issued with dsc9513CounterControl().

{% tabs %}
{% tab title=" Input Parameters" %}
| Name    | Description                           |
| ------- | ------------------------------------- |
| DSCB    | The handle of the board to operate on |
| Counter | Counter no., 1-10 for GPIO-MM-11      |
| Value   | 16-bit load value, range 0-65535      |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
