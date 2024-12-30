# dscDASetSettings

```c
BYTE dscDASetSettings(DSCB board, DSCDASETTINGS* dasettings);
```

Sets the D/A configuration for future D/A conversions. A delay of approximately 10 microseconds occurs during this function call in order to allow the analog circuit on the board to settle on the new settings. On -AT (auto-calibrating) boards, if dasettings->load\_cal is TRUE, then load the D/A calibration settings from the EEPROM for the current D/A configuration. This results in slightly more accurate D/A conversions but causes an additional, longer delay of approximately 10 milliseconds.

This function is ONLY supported by the Hercules II EBX, Helios and DS-MPE-DAQ0804.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**                                                       | **Description**                                                                                                            |
| -------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| DSCB                                                           | The handle of the board to operate on                                                                                      |
| [DSCDASETTINGS](../15.-structure-definitions/dscdasettings.md) | The D/A conversion settings to be used in subsequent D/A conversions; these settings will be used for all D/A conversions. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
