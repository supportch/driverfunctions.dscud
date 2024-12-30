# dscAACGetStatus

```c
BYTE dscAACGetStatus(DSCB board, DSCAACSTATUS* status)
```

Gets the status of the auto auto-calibration operation and registers

{% tabs %}
{% tab title=" Input Parameters" %}
| Name                                                         | Description                               |
| ------------------------------------------------------------ | ----------------------------------------- |
| DSCB                                                         | The handle of the board to operate on     |
| [DSCAACSTATUS](../15.-structure-definitions/dscaacstatus.md) | Status of the AAC operation and registers |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
