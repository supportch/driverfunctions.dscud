# dscAACCommand

```c
#define AAC_CMD_HOLD 0x10
#define AAC_CMD_REL 0x08
#define AAC_CMD_RESET 0x04
#define AAC_CMD_ABORT 0x02
#define AAC_CMD_TRIG 0x01 DWORD

BYTE dscAACCommand(DSCB board, DWORD cmd)
```

Sets the commands for auto auto-calibration. These commands can be used to enable, disable, trigger, and reset the auto auto-calibration

{% tabs %}
{% tab title=" Input Parameters" %}
| Name | Description                                                                                        |
| ---- | -------------------------------------------------------------------------------------------------- |
| DSCB | The handle of the board to operate on                                                              |
| Cmd  | Command used to enable, disable, trigger, and reset auto auto-calibration. Masks are AAC\_CMD\_XXX |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
