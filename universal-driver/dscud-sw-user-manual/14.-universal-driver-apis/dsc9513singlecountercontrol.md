# dsc9513SingleCounterControl

```c
BYTE dsc9513SingleCounterControl(DSCB board, BYTE counter, BYTE action)
```

Initiates a Load, Arm, Load & Arm, Disarm, Save, or Disarm & Save command on a single counter on GPIO-MM-11 or GPIO-MM-12. See information on the commands in dsc9513CounterControl ().

{% tabs %}
{% tab title=" Input Parameters" %}
| Name    | Description                                                                                                                                                    |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DSCB    | The handle of the board to operate on                                                                                                                          |
| counter | Counter no., 1-10 for GPIO-MM-11 and GPIO-MM-12                                                                                                                |
| action  | Action to perform on the selected counter. Select from choices below: QMM\_ACTION\_NONE 0 QMM\_ACTION\_ARM 1 QMM\_ACTION\_LOAD 2 QMM\_ACTION\_LOAD\_AND\_ARM 3 |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
