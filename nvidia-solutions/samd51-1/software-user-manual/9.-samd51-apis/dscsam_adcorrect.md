# DSCSAM\_ADCorrect

This function get the A/D raw voltage, A/D channel number and calculates the corrected A/D voltage using respective A/D channel calibration factors and return the corrected voltage to caller.

```
double DSCSAM_ADCorrect (BYTE ad_channel, double ad_raw_voltage);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**         | Description     |
| ---------------- | --------------- |
| ad\_channel      | 0 - 5           |
| ad\_raw\_voltage | A/D raw voltage |
{% endtab %}
{% endtabs %}

| Return Value          |   |
| --------------------- | - |
| A/D Corrected voltage |   |
