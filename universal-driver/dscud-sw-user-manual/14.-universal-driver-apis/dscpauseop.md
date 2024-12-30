# dscPauseOp

```c
BYTE dscPauseOp(DSCB board)
```

This function pauses A/D interrupts by turning off the interrupt enable and stopping the A/D clock. This holds the A/D channel counter and FIFO at their current positions.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                       |
| -------- | ------------------------------------- |
| DSCB     | The handle of the board to operate on |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
