# dscDIOSetConfig

```c
BYTE dscDIOSetConfig(DSCB board, BYTE* config_bytes);
```

Sets the DIO port configuration for future DIO operations.

Note: See board user manual or 82C55 datasheet (if applicable) for config\_byte details.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**      | **Description**                                                                                                                                             |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DSCB          | The handle of the board to operate on                                                                                                                       |
| config\_bytes | The value(s) used to configure the digital I/O ports. See each board's user manual for information on the number and definition of the configuration bytes. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
