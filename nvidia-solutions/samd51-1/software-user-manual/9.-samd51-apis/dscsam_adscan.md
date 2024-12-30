# DSCSAM\_ADScan

This function executes one A/D scan (sample on all channels between Lowch and Highch). It uses all existing A/D settings on the board. It assumes that the board is configured for scan mode, not sample mode.

```c
BYTE DSCSAM_ADScan(SWORD* Sample);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | Description                                                                            |
| -------- | -------------------------------------------------------------------------------------- |
| Sample   | Address to buffer of type unsigned int to store the sample resulting from the A/D scan |
{% endtab %}
{% endtabs %}

| Return Value     |   |
| ---------------- | - |
| Error code or 0. |   |
