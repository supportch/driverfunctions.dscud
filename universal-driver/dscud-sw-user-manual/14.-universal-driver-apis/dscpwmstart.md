# dscPWMStart

```c
BYTE dscPWMStart(DSCB board, DSCPWM *pwmCircuit);
```

This function is used to start a PWM circuit on the MPE-GPIO. Please consult the MPE-GPIO for more information on the PWM circuit.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**                                          | **Description**                                            |
| ------------------------------------------------- | ---------------------------------------------------------- |
| DSCB                                              | The board handle                                           |
| [DSCPWM ](../15.-structure-definitions/dscpwm.md) | Pointer to the DSCPWM struct containing the PWM parameters |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
