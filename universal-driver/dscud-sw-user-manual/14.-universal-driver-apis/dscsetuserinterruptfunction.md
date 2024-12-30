# dscSetUserInterruptFunction

```c
BYTE dscSetUserInterruptFunction(DSCB board,DSCUSERINTFUNCTION* dscuserintfunction);
```

Installs a user-provided function attached to all interrupt types for later execution either alone or in conjunction with another driver interrupt function. In DOS, the user-provided function may not call other Universal Driver functions to operate on the board, since at the time of execution the board will be locked by the driver and unavailable to the function. In other operating systems this restriction does not apply.

{% tabs %}
{% tab title="Input Parameters" %}
| Name                                                                     | Description                                                                                                                                                       |
| ------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DSCB                                                                     | The handle of the board to operate on                                                                                                                             |
| [DSCUSERINTFUNCTION](../15.-structure-definitions/dscuserintfunction.md) | Data structure containing information on the user interrupt function. See the definition [DSCUSERINTFUNCTION](../15.-structure-definitions/dscuserintfunction.md) |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
