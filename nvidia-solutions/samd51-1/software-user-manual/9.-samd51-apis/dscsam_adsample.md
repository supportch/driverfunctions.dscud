# DSCSAM\_ADSample

This function executes one A/D conversion using the current board settings. It does not perform any configuration of the board but rather uses the current settings. It assumes that the board is configured for sample mode, not scan mode.

```c
BYTE DSCSAM_ADSample(SWORD* Sample);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name   | Description                                                                                  |
| ------ | -------------------------------------------------------------------------------------------- |
| Sample | Address to buffer of type unsigned int to store the sample resulting from the A/D conversion |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
