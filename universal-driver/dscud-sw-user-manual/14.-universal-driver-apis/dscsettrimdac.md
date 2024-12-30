# dscSetTrimDac

```c
BYTE dscSetTrimDac(DSCB board, DWORD trimDac, BYTE value)
```

This function modifies the onboard autocalibration TrimDACs for all -AT boards and the Hercules-II. This function should be called only for debugging or advanced use, as improper values will throw the board out of calibration.

{% tabs %}
{% tab title="Input Parameters" %}
| Name    | Description                                  |
| ------- | -------------------------------------------- |
| DSCB    | The handle of the board to operate on        |
| trimDac | Which TrimDAC (0-7) to modify                |
| value   | 8-bit data to write to the specified TrimDAC |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
