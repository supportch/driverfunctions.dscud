# dscCancelOp

```c
BYTE dscCancelOp(DSCB board)
```

Terminates all currently running interrupt operations on the board. If there is no current interrupt operation on the board (OP\_TYPE\_NONE), the function will return DE\_NONE\_IN\_PROGRESS.

{% tabs %}
{% tab title="Input Parameters" %}
| Name | Description                           |
| ---- | ------------------------------------- |
| DSCB | The handle of the board to operate on |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
