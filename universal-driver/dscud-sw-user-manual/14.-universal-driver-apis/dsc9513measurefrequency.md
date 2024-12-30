# dsc9513MeasureFrequency

```c
BYTE dsc9513MeasureFrequency(DSCB board, BYTE interval, BYTE source, WORD* pulses)
```

This function uses counters 4 and 5 to measure the frequency of a TTL-level signal. The input signal can be connected to any of the nine sources listed below. In order for this function to run, Counter 4 output (pin 12) must be wired externally to Counter 5 gate (pin 15). Otherwise, the program will hang.

The output of Counter 4 is initially high, and the output of Counter 5 is initially low. Counter 4's output will remain high for the duration specified in interval. The frequency is measured by using Counter 5 to count the number of rising edges of the input signal which occur during this measured time interval, and the count is returned in pulses. Counter 5 is gated by the output of Counter 4, so it counts for a known period of time. If the measurement period is too long, Counter 5 will reach its maximum count of 65535, its output will toggle high, and the function will return an error code of DE\_QMM\_OVERFLOW.&#x20;

Thus the programmer has both a hardware and a software indication of overflow. In this case use the next smaller measurement interval and try again, continuing in this fashion until no error code is returned. The entire procedure lasts exactly as long as the specified measurement interval. For the longest interval (10 seconds), the computer may appear to have hung; however, it is simply in a monitoring loop waiting for Counter 4's output to toggle low, and it will return to the calling program as soon as this event occurs.

The fastest measurable frequency is limited by the 9513 chip specifications to 7MHz; specifying a measurement interval of 1 ms for a 7MHz input frequency will yield a count of 7000, well within the 65535 count limit. The slowest measurable frequency depends on the allowable error tolerance, since the edge count could be off by 1 due to alignment of the input edges with the measurement interval.

Measuring the frequency of a very slow signal is more accurately done by measuring the period with dsc9513MeasurePeriod() and taking the reciprocal. The frequency of the input signal is derived from the formulas Frequency = pulses / Measurement period or Frequency = pulses \* Measurement frequency The function will return DE\_QMM\_OVERFLOW if a measurement overflow occurred. Otherwise it will return DE\_NONE .

{% tabs %}
{% tab title=" Input Parameters" %}
| Name     | Description                                                                                                            |
| -------- | ---------------------------------------------------------------------------------------------------------------------- |
| DSCB     | The handle of the board to operate on                                                                                  |
| Interval | Desired measurement time interval. See the table below.                                                                |
| Source   | Source signal to measure. See the table below Note that Gate 5 is not a valid choice since it is used by the function. |
| Pulses   | Pointer to a variable that will contain the number of pulses                                                           |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

{% tabs %}
{% tab title="QMM Interval Table" %}
| Macro                      |
| -------------------------- |
| QMM\_INTERVAL\_1MS\_1KHZ   |
| QMM\_INTERVAL\_10MS\_100HZ |
| QMM\_INTERVAL\_100MS\_10HZ |
| QMM\_INTERVAL\_1S\_1HZ     |
| QMM\_INTERVAL\_10S\_01HZ   |
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="QMM Source Table" %}
| Macro              |
| ------------------ |
| QMM\_SOURCE\_SRC1  |
| QMM\_SOURCE\_SRC2  |
| QMM\_SOURCE\_SRC3  |
| QMM\_SOURCE\_SRC4  |
| QMM\_SOURCE\_SRC5  |
| QMM\_SOURCE\_GATE1 |
| QMM\_SOURCE\_GATE2 |
| QMM\_SOURCE\_GATE3 |
| QMM\_SOURCE\_GATE4 |
{% endtab %}
{% endtabs %}
