# dscDASetSim

```c
BYTE dscDASetSim(DSCB board, BOOL sim);
```

This function configures the board for simultaneous update or regular single-channel update mode. Updating a DAC may be done in either single-channel mode or simultaneous update mode.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                                              |
| -------- | ------------------------------------------------------------ |
| DSCB     | The handle of the board to operate on                        |
| sim      | 0 = single-channel update mode, 1 = simultaneous update mode |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
