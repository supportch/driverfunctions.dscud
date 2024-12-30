# dscDIOInputBit

```c
BYTE dscDIOInputBit(DSCB board, BYTE port, BYTE bit, BYTE* digital_value);
```

Receives a bit value from a given digital input port at a specified bit location (0-7). If port exceeds the board's maximum number of digital ports, the function returns DE\_INVALID\_PARM. If the board contains only a single digital port, then this value is ignored.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**       | **Description**                                       |
| -------------- | ----------------------------------------------------- |
| DSCB           | The handle of the board to operate on                 |
| port           | Selected input port                                   |
| bit            | Bit location (0-7) to read on the selected input port |
| digital\_value | Present value of the bit read; 1 or 0                 |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
