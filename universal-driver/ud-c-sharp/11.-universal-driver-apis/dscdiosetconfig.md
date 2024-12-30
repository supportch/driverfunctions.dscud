# dscDIOSetConfig()

```c
byte dscDIOSetConfig(short board, ref byte config);
```

Sets the DIO port configuration for future DIO operations.

Note: See board user manual or 82C55 datasheet (if applicable) for config\_byte details.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name** | **Description**                                                                                                                                                                                                                                                                                   |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| board    | The handle of the board to operate on                                                                                                                                                                                                                                                             |
| config   | <p>The value(s) used to configure the digital I/O ports. See each board's user manual for information on the number and definition of the configuration bytes. <br>0x0- Port A&#x26;B input</p><p>0x1-Port A output, B input</p><p>0x2-Port A input, B output</p><p>0x0- Port A&#x26;B output</p> |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
