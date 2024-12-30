# dscCounterSetRateSingle()

```csharp
COUNTER_0 = 0x00
COUNTER_0_1 = 0x08

byte dscCounterSetRateSingle(short board, float hertz, UInt32 ctr);
```

This function sets the output frequency of the specified counter or counter combination (instead of all onboard counters.)

{% tabs %}
{% tab title=" Input Parameters" %}
| Name  | Description                                            |
| ----- | ------------------------------------------------------ |
| board | The handle of the board to operate on                  |
| herts | Desired rate for the A/D counter/timer circuit         |
| ctr   | The desired counter or counter combination to program. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
