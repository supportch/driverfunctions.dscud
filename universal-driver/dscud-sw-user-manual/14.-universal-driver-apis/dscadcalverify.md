# dscADCalVerify

```c
BYTE dscADCalVerify(DSCB board, DSCADCALPARAMS* params)
```

Verifies the accuracy of the most recent A/D autocalibration process and returns the maximum measured errors. If params->adrange is not set to a valid A/D range code, the function returns the error code DE\_INVALID\_PARM. The calibration verification process lasts approx. 2-5 seconds.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**                                                         | **Description**                                                     |
| ---------------------------------------------------------------- | ------------------------------------------------------------------- |
| DSCB                                                             | The handle of the board to operate on                               |
| [DSCADCALPARAMS](../15.-structure-definitions/dscadcalparams.md) | The A/D calibration settings to be used in the verification process |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

