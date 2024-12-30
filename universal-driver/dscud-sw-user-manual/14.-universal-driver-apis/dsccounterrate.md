# dscCounterRate

```c
BYTE dscCounterRate(DSCB board, DSCCR *ctr);
```

This function programs a counter for timer mode with down counting. The counter is started immediately. This is a streamlined function intended to provide a convenient way to program a counter/timer for the most common needs. This function is implemented only in DS-MPE-GIO, DS-MPE-DAQ0804, ARIES, P104-GPIO96, Ruby-MM-1616, ZETA and HELIX.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**                                        | **Description**                                                            |
| ----------------------------------------------- | -------------------------------------------------------------------------- |
| DSCB                                            | The handle of the board to operate on                                      |
| [DSCCR ](../15.-structure-definitions/dsccr.md) | The settings for all counters in the structure dsccr; see DSCCR definition |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
