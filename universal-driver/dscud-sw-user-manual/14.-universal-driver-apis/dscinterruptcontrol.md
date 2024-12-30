# dscInterruptControl

```c
BYTE DSCUDAPICALL dscInterruptControl(DSCB board, BYTE* config_byte)
```

Controls GPIO11 interrupt configuration such as clear flipflop, disable and enable interrupt.

{% tabs %}
{% tab title="Input Parameters" %}
| Name         | Description                                            |
| ------------ | ------------------------------------------------------ |
| DSCB         | The handle of the board to operate on                  |
| config\_byte | a pointer to control the interrupt selections on board |
{% endtab %}
{% endtabs %}

| Return Value           |
| ---------------------- |
| Error code or DE\_NONE |
