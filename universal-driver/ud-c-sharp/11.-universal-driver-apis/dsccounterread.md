# dscCounterRead()

```c
byte dscCounterRead(short board, ref DSCCR dsccr);
```

Reads the data from an 82C54 counter.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                                                            |
| -------- | -------------------------------------------------------------------------- |
| board    | The handle of the board to operate on                                      |
| DSCCR    | The settings for all counters in the structure dsccr; see DSCCR definition |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
