# dscADIntCancel

```c
BYTE dscADIntCancel(DSCB board)
```

This function stops A/D interrupts by turning off the interrupt enable, stopping the A/D clock, and removing the A/D interrupt handler.

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
