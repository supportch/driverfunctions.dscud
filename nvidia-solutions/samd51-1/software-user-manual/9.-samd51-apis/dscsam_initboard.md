# DSCSAM\_InitBoard

This function initializes the SPI driver, BUSY GPIO, read the A/D, D/A calibration constants, read the board type and return to application.

```c
BYTE DSCSAM_InitBoard(BYTE * Board_type)
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name        | Description                                                                                        |
| ----------- | -------------------------------------------------------------------------------------------------- |
| Board\_type | <p>pointer to receive board type</p><p>(0 - Ziggy, 1 - TBD, 3 - Stevie, 5 - Elton, 7 - Jethro)</p> |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
