# dscDIOInputByte()

```c
byte dscDIOInputByte(short board, byte port, ref byte digital_value);
```

Receives a BYTE from a given digital input port.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**       | **Description**                                                          |
| -------------- | ------------------------------------------------------------------------ |
| board          | The handle of the board to operate on                                    |
| port           | Selected input port                                                      |
| digital\_value | The BYTE value read from the selected digital input port; range is 0-255 |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
