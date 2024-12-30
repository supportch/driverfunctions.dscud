# dscDAAutoCal

```c
BYTE dscDAAutoCal(DSCB board, DSCDACALPARAMS* params);
```

Performs a D/A auto-calibration. This function incurs a delay of 2-5 seconds in order to perform the D/A auto-calibration process.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name                                                             | Description                                                                                                     |
| ---------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| DSCB                                                             | The handle of the board to operate on                                                                           |
| [DSCDACALPARAMS](../15.-structure-definitions/dscdacalparams.md) | The AD/A calibration settings to be used in the auto-calibration process. See the definition of DSCADCALPARAMS. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
