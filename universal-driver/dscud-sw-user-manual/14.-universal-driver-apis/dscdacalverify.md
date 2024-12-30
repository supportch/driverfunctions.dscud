# dscDACalVerify

```c
BYTE dscDACalVerify(DSCB board, DSCDACALPARAMS* params);
```

Verifies the accuracy of the most recent D/A auto-calibration process and returns the measured errors.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name                                                             | Description                                                         |
| ---------------------------------------------------------------- | ------------------------------------------------------------------- |
| DSCB                                                             | The handle of the board to operate on                               |
| [DSCDACALPARAMS](../15.-structure-definitions/dscdacalparams.md) | The D/A calibration settings to be used in the verification process |
{% endtab %}
{% endtabs %}

These variables of the passed DSCDACALPARAMS structure are modified:

| Name   | Description                                                           |
| ------ | --------------------------------------------------------------------- |
| offset | Error in D/A LSB counts at the mid-scale of the D/A range             |
| gain   | Error in D/A LSB counts at the full-scale (high end) of the D/A range |

| Return Value     |
| ---------------- |
| Error code or 0. |
