# dscADScanInt

```c
BYTE dscADScanInt(DSCB board, DSCAIOINT* dscaioint);
```

Performs A/D scans using interrupt-based I/O with one scan per A/D clock tick. Note that calling this function only starts the interrupt operations in a separate system thread. The function call does not result in an atomic transaction with immediate results. Rather, it starts a real-time process that terminates only when the number of conversions reaches the maximum specified (one-shot mode) or if a call to dscCancelOp() is made.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name                                                   | Description                                        |
| ------------------------------------------------------ | -------------------------------------------------- |
| DSCB                                                   | The handle of the board to operate on              |
| [DSCAIOINT](../15.-structure-definitions/dscaioint.md) | The interrupt-based analog I/O settings to be used |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
