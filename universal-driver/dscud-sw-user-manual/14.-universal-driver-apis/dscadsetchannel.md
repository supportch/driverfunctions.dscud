# dscADSetChannel

```c
BYTE dscADSetChannel(DSCB board, BYTE low_channel, BYTE high_channel);
```

Sets the input channel range for future A/D conversions. A slight delay of approximately 10 microseconds occurs during this function call in order to allow the analog circuit on the board to settle on the new settings.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name          | Description                                       |
| ------------- | ------------------------------------------------- |
| DSCB          | The handle of the board to operate on             |
| low\_channel  | The low channel in the desired range of channels  |
| high\_channel | The high channel in the desired range of channels |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
