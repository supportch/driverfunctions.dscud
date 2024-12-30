# dscDAAutoCal()

```c
byte dscDAAutoCal(short board, ref DSCDACALPARAMS DACALparam);
```

Performs a D/A auto-calibration. This function incurs a delay of 2-5 seconds in order to perform the D/A auto-calibration process.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name           | Description                                                                                                     |
| -------------- | --------------------------------------------------------------------------------------------------------------- |
| board          | The handle of the board to operate on                                                                           |
| DSCDACALPARAMS | The AD/A calibration settings to be used in the auto-calibration process. See the definition of DSCADCALPARAMS. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
