# dscGetStatus

```c
BYTE dscGetStatus(DSCB board, DSCS* status)
```

Returns the current status of any interrupt operations. This includes both the operation type (OP\_TYPE\_NONE or OP\_TYPE\_INT) and the current number of interrupts. On boards containing a FIFO (-AT boards and Prometheus), if the FIFO has overflowed, dscGetStatus() will reset the FIFO allowing interrupt operation to proceed. If interrupt operation has concluded (i.e., the current number of transfers has reached the maximum specified and one-shot mode has been specified) then dscGetStatus() will terminate interrupt processing.

{% tabs %}
{% tab title="Input Parameters" %}
| Name                                         | Description                                               |
| -------------------------------------------- | --------------------------------------------------------- |
| DSCB                                         | The handle of the board to operate on                     |
| [DSCS](../15.-structure-definitions/dscs.md) | Data structure used to store the current operation status |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
