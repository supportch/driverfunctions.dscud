# DSCSAM\_DAConvert

This function outputs a value to a single D/A channel.

```c
BYTE DSCSAM_DAConvert(BYTE Channel, unsigned int DACode, BYTE Loadcal);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name    | Description                                              |
| ------- | -------------------------------------------------------- |
| Channel | 0-1                                                      |
| DACode  | 0-4095                                                   |
| Loadcal | 0 - User specified DACode will be written on D/A channel |
|         | 1 - Corrected D/A code will be written on D/A channel    |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
