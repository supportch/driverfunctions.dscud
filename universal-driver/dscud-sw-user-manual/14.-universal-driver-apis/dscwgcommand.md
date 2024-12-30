# dscWGCommand

```c
#define WG_CMD_START 0x01
#define WG_CMD_PAUSE 0x02
#define WG_CMD_RESET 0x04
#define WG_CMD_INC 0x08
BYTE dscWGCommand(DSCB board, DWORD cmd)
```

Commands to start, stop, reset, and trigger the D/A wave form generator

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                                                                                                     |
| -------- | ------------------------------------------------------------------------------------------------------------------- |
| DSCB     | The handle of the board to operate on                                                                               |
| cmd      | Command to stop, start, reset, and trigger D/A wave form generator. Defines can be found in DSCUD.H as WG\_CMD\_XXX |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
