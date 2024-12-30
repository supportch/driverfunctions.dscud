# dsc9513SpecialCounterFunction

```c
BYTE dsc9513SpecialCounterFunction(DSCB board, DSCQMMSCF* dscqmm_scf)
```

This function is used to program the alarm registers for counters 1 and 2 of each 9513 chip, to set the initial output state of any counter, or to step (increment / decrement) any counter. The most common use is to set the initial output state of a counter operating in toggle mode.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name      | Description                                                          |
| --------- | -------------------------------------------------------------------- |
| DSCB      | The handle of the board to operate on                                |
| DSCQMMSCF | Structure containing data required for the special counter function. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
