# dscADSetSettings

```c
BYTE dscADSetSettings(DSCB board, DSCADSETTINGS* adsettings);
```

Sets the A/D configuration for future A/D conversions. A delay of approximately 10 microseconds occurs during this function call in order to allow the analog circuit on the board to settle on the new settings. On -AT (auto-calibrating) boards, if adsettings->load\_cal is TRUE, then load the A/D calibration settings from the EEPROM for the current A/D range. This results in slightly more accurate A/D conversions but causes an additional, longer delay of approximately 10 milliseconds.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**                                                       | **Description**                       |
| -------------------------------------------------------------- | ------------------------------------- |
| DSCB                                                           | The handle of the board to operate on |
| [DSCADSETTINGS](../15.-structure-definitions/dscadsettings.md) | The A/D scan settings to be used      |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
