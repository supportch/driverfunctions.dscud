# dscADClockConfig

```c
BYTE dscADClockConfig(DSCB board, BYTE adclk)
```

This function configures the clock source for A/D conversions.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                                                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| DSCB     | The handle of the board to operate on                                                                                               |
| adclk    | int 0-3 ; 0 = software command (ADSample or ADScan function), 1 = falling edge on DIO0, 2 = counter 0 output, 3 = counter 1 output. |
{% endtab %}
{% endtabs %}

| Return Value                   |
| ------------------------------ |
| <p></p><p>Error code or 0.</p> |
