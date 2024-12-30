# dscCounterRead

```c
BYTE dscCounterRead(DSCB board, DSCCR* dsccr);
```

Reads the data from an 82C54 counter.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**                                       | **Description**                                                            |
| ---------------------------------------------- | -------------------------------------------------------------------------- |
| DSCB                                           | The handle of the board to operate on                                      |
| [DSCCR](../15.-structure-definitions/dsccr.md) | The settings for all counters in the structure dsccr; see DSCCR definition |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
