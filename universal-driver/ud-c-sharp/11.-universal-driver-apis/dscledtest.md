# dscLEDTest()

```c
byte dscLEDTest(short dscb, int enable);
```

This function turns the LED on or off.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                       |
| -------- | ------------------------------------- |
| board    | The handle of the board to operate on |
| Enable   | 1 = LED ON, 0 = LED OFF               |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
