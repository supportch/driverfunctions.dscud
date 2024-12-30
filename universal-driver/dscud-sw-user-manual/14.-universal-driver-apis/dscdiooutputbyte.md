# dscDIOOutputByte

```c
BYTE dscDIOOutputByte(DSCB board, BYTE port, BYTE digital_value);
```

Sends a BYTE to a given digital output port.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**       | **Description**                                               |
| -------------- | ------------------------------------------------------------- |
| DSCB           | The handle of the board to operate on                         |
| Port           | Selected output port                                          |
| digital\_value | The value to write to the digital output port; range is 0-255 |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
