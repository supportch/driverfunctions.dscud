# dscCounterReset

```c
BYTE dscCounterReset(DSCB board, BYTE ctrno);
```

This function resets a counter. When a counter is reset, it stops running, all its registers are cleared to 0, and any DIO line used for input or output is released back to normal DIO operation.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                       |
| -------- | ------------------------------------- |
| DSCB     | The handle of the board to operate on |
| ctrno    | Counter number to reset               |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

