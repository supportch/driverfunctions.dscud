# dscCounterSetRate

```c
BYTE dscCounterSetRate(DSCB board, float rate);
```

Sets the output frequency of the counter/timers dedicated to A/D sample rate timing. On all Diamond-MM boards, counters 1 and 2 are used together (2 x 16 bits) for A/D timing, and this function will program both counters such that the output of counter 2 is as close as possible to the selected rate. On Prometheus, counter 0 (24 bits) is used for A/D timing. Note that not all rates are possible with complete precision. Each rate is set by programming the counter(s) with the divisor(s) resulting from the calculation (Input Clock) / Rate. On Diamond-MM boards, Input Clock is usually 10MHz. In each case a best fit is determined. However because of the integer math used, any errors resulting from truncation of the divisor to an integer value will cause the actual rate to differ from the desired rate. If rate < 1.0 then the function returns DE\_INVALID\_PARM. This function works on all boards with 82C54 counter/timer chips. Quartz-MM uses a different counter/timer chip and has separate functions for programming.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name | Description                                    |
| ---- | ---------------------------------------------- |
| DSCB | The handle of the board to operate on          |
| rate | Desired rate for the A/D counter/timer circuit |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
