# dscSpecialFunction

```c
BYTE dscSpecialFunction(DSCB board, DSCSPECIALFUNC *gpioconfig, DSCGPIOCONFIG);
```

This function performs special function operations for specific boards. For example, in DSC\_MPEGPIO and DS-MPE-DAQ0804, the GPIO pull up and pull down configuration can be done using the dscSpecialFunction as mentioned below.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**                                                          | **Description**                                                     |
| ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| DSCB                                                              | The handle of the board to operate on                               |
| [DSCSPECIALFUNC ](../15.-structure-definitions/dscspecialfunc.md) | The special function settings to be used in the GPIO config process |
| DSCGPIOCONFIG                                                     | Macro to indicate the GPIO configuration process in DSC\_MPEGPIO    |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
