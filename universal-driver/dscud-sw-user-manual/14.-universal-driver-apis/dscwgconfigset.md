# dscWGConfigSet

```c
BYTE dscWGConfigSet(DSCB board, DSCWGCONFIG* config)
```

Configures D/A wave form generator. Sets the depth, number of output per trigger, and trigger source.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**                                                   | **Description**                                                            |
| ---------------------------------------------------------- | -------------------------------------------------------------------------- |
| DSCB                                                       | The handle of the board to operate on                                      |
| [DSCWGCONFIG](../15.-structure-definitions/dscwgconfig.md) | Structure containing configuration information for D/A wave form generator |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
