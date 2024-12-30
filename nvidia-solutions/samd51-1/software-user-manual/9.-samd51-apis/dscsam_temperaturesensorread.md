# DSCSAM\_TemperatureSensorRead

This function reads the SAM device temperature.

```c
BYTE DSCSAM_TemperatureSensorRead(int* Data);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name | Description                                                         |
| ---- | ------------------------------------------------------------------- |
| Data | pointer to receive the temperature (temperature in degrees Celsius) |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
