# dscWatchdogDisable

```c
BYTE dscWatchdogDisable(DSCB board);
```

This function disables the watchdog timer circuit on the specified board. A previously enabled but subsequently disabled watchdog timer may be re-enabled using the existing configuration by a subsequent call to dscWatchdogTrigger().

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**  |
| -------- | ---------------- |
| DSCB     | The board handle |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
