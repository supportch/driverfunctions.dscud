# dscWatchdogEnable

```c
BYTE dscWatchdogEnable(DSCB board, WORD wd1, BYTE wd2, SDWORD options);
```

This function loads the watchdog counters to the specified values and configures the general behavior of watchdog counter 1, and arms the watchdog timer circuit.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name** | **Description**                         |
| -------- | --------------------------------------- |
| DSCB     | The board handle                        |
| wd1      | Counter value for first watchdog timer  |
| wd2      | Counter value for second watchdog timer |
| options  | A bitwise OR of watchdog options        |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
