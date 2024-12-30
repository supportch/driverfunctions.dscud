# dscADIntStatus

```c
BYTE dscADIntStatus(DSCB board, DSCADINTSTATUS* adintstatus);
```

This function returns the interrupt routine status including running or not running, number of conversions completed, cycle mode, FIFO status, and FIFO flags.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**                                                           | **Description**                                                                                                                      |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| DSCB                                                               | The handle of the board to operate on                                                                                                |
| [DSCADINTSTATUS](../15.-structure-definitions/dscadintstatus-1.md) | The A/D interrupt status such as interrupt routine, number of conversions, cycle mode, FIFO status and FIFO flags can be determined. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
