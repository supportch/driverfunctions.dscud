# dsc9513MeasurePeriod

```c
BYTE dscQMMMeasurePeriod(DSCB board, BYTE frequency, DWORD* periods);
```

This function measures the period of an input signal by counting the number of pulses of a known reference frequency which occur between two successive rising edges of the input signal. The input signal is connected to Gate 5 (pin 15), and the counting frequency is selected by frequency. The accuracy of the measurement is equal to the period of the chosen reference frequency.

The function operates as follows: Counter 5's output is preset low. On the first rising edge of the input signal, Counter 5 will begin to count edges of the reference frequency, and on the second rising edge its count will be transferred into its hold register. The contents of the hold register are returned in the parameter periods and represents the number of edges, or periods, of the reference frequency equal to a single period of the input signal. Note that since only the rising edge of the input signal is used to control Counter 5, the input signal's duty cycle is irrelevant. Also note that the function waits for the first rising edge before beginning the measurement. This adds to the total execution time for the function.

If the signal's period is too long, Counter 5 will reach its maximum count of 65535 and its output will toggle high. In this case the function will return error code DE\_QMM\_OVERFLOW, and periods will be set to 0. To correct this situation, select the next slower count frequency and repeat the procedure in this fashion until no error code is returned. The longest period which can be measured using this function is 65,535 x the period of the chosen reference frequency. In the case of 400Hz, the slowest option, the longest period is 163,837ms, or 2 mins. 44 secs. Since the fastest reference frequency is 4MHz, the smallest period which can be captured is greater than the period of this frequency, or 0.25μs. However the measurement error will increase substantially as the period of the input signal approaches this lower limit.

Measuring the period of a fast input signal is more accurately done by measuring the frequency instead with Dsc9513MeasureFrequency() and taking the reciprocal.

The period of the input signal is calculated by the formula: Period = periods \* reference period

The function will return DE\_QMM\_OVERFLOW if a measurement overflow occurred. Otherwise it will return DE\_NONE .

{% tabs %}
{% tab title=" Input Parameters" %}
| Name      | Description                                                                                  |
| --------- | -------------------------------------------------------------------------------------------- |
| DSCB      | The handle of the board to operate on                                                        |
| Frequency | The desired reference interval of frequency to use for the measurement. See the table below. |
| Periods   | Pointer to a variable to hold the result of the measurement                                  |
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
