# dscADSetScan

```c
BYTE dscADSetScan(DSCB board, DSCADSCAN* dscadscan)
```

Sets the A/D configuration for scan settings.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name                                                     | Description                           |
| -------------------------------------------------------- | ------------------------------------- |
| DSCB                                                     | The handle of the board to operate on |
| [DSCADSCAN](../15.-structure-definitions/dscadscan-1.md) | The A/D scan settings to be used      |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
