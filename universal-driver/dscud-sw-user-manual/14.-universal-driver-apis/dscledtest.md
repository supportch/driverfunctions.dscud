# dscLEDTest

```c
BYTE dscLEDTest(DSCB board, BOOL state);
```

This function turns the LED on or off.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                       |
| -------- | ------------------------------------- |
| DSCB     | The handle of the board to operate on |
| State    | 1 = LED ON, 0 = LED OFF               |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
