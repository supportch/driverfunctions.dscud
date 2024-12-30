# dscADSetTiming

```c
BYTE dscADSetTiming(DSCB board, DSCADSETTINGS* adsettings);
```

This function configures the A/D clock source and scan settings.

{% tabs %}
{% tab title="Input Parameters" %}
| Name          | Description                                                                                                                                                                                                                        |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DSCB          | The handle of the board to operate on                                                                                                                                                                                              |
| DSCADSETTINGS | The A/D conversion settings to be used in subsequent A/D conversions; these settings will be used for all A/D conversions until they are changed with dscADSetChannel() or a call to an A/D interrupt function. See DSCADSETTINGS. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
