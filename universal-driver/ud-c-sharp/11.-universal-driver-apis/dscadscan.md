# dscADScan()

```c
byte dscADScan(short board, ref DSCADSCAN dscadscan, IntPtr sample_values);
```

Performs a single A/D conversion on each channel in the selected channel range. The channels are sampled individually in rapid sequence. The channels are not sampled simultaneously. The high channel number must be greater than or equal to the low channel number, and both values must be less than the total number of channels on the board. Setting high = low is the same as using DscADSample. The function returns DE\_OPERATION\_TIMED\_OUT if a timeout occurs because the A/D circuit is not ready (A/D Busy signal stays true). This usually indicates a hardware error.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**       | **Description**                                                      |
| -------------- | -------------------------------------------------------------------- |
| board          | The handle of the board to operate on                                |
| DSCADSCAN      | The A/D scan settings to be used                                     |
| sample\_values | Pointer to an array or allocated memory for holding the scan values. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
