# dscCounterDirectSet

```c
BYTE dscCounterDirectSet(DSCB board, BYTE code, WORD data, BYTE ctr_number);
```

Sets the configuration for an individual counter on an 82C54 chip. This chip is used on all boards with counter/timers except Quartz-MM and Prometheus. This function provides direct access to the 82C54 configuration register, enabling functionality other than simple rate generator. For information on the possible configuration data, see the 82C54 datasheet included with each board's user manual.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name        | Description                                                                                                                                          |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| DSCB        | The handle of the board to operate on                                                                                                                |
| code        | The configuration code to write to the 82C54 chip; see the 82C54 datasheet at the back of the board's user manual for configuration code information |
| data        | The initial count to write to the selected counter; range is 0-65535                                                                                 |
| ctr\_number | The individual counter to set; range is 0-2                                                                                                          |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

