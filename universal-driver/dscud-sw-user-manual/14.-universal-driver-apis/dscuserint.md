# dscUserInt

```c
BYTE dscUserInt(DSCB board, DSCUSERINT* dscuserint, DSCUserInterruptFunction func);
```

Starts execution of a user interrupt function alone (without another driver interrupt function).

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**                                                   | **Description**                                                                 |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------- |
| DSCB                                                       | The handle of the board to operate on                                           |
| [DSCUSERINT](../15.-structure-definitions/dscuserint-1.md) | Structure containing configuration information for the user interrupt operation |
| DSCUserInterruptFunction                                   | The name of the user interrupt function                                         |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
