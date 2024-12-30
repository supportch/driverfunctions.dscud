# dscCounterSetRateSingle

```c
#define COUNTER_0 0x01
#define COUNTER_1 0x02
#define COUNTER_2 0x04
#define COUNTER_0_1 0x08
#define COUNTER_1_2 0x10
#define COUNTER_0_1_2 0x20

BYTE dscCounterSetRateSingle(DSCB board, float rate, DWORD ctr);
```

This function is similar to DscCounterSetRate() except that it operates only on the specified counter or counter combination (instead of all onboard counters.)

{% tabs %}
{% tab title=" Input Parameters" %}
| Name | Description                                            |
| ---- | ------------------------------------------------------ |
| DSCB | The handle of the board to operate on                  |
| rate | Desired rate for the A/D counter/timer circuit         |
| ctr  | The desired counter or counter combination to program. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
