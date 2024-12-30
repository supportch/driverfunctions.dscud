# dscFifoStatus

```c
BYTE dscFifoStatus(DSCB board, DSCFIFO* Fifo)
```

This function will read current status of FIFO and store all the values of structure variables.

{% tabs %}
{% tab title="Input Parameters" %}
| Name                                               | Description                                                          |
| -------------------------------------------------- | -------------------------------------------------------------------- |
| DSCB                                               | The handle of the board to operate on                                |
| [DSCFIFO](../15.-structure-definitions/dscfifo.md) | [DSCFIFO ](../15.-structure-definitions/dscfifo.md)structure pointer |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

