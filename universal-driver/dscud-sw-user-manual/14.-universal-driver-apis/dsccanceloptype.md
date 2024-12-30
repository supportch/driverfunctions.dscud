# dscCancelOpType

```c
BYTE dscCancelOpType(DSCB board, DWORD int_type);
```

Terminates a currently running interrupt operation on the board based on int\_type. If there is no current interrupt operation on the board matching the interrupt type, the function will return DE\_NONE\_IN\_PROGRESS.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**  | **Description**                                 |
| --------- | ----------------------------------------------- |
| DSCB      | The handle of the board to operate on           |
| int\_type | The interrupt type (one of INTTYPE\*) to cancel |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

**DSCB**&#x20;

SWORD
