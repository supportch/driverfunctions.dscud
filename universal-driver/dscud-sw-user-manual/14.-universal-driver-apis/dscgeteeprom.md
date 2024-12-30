# dscGetEEPROM

```c
BYTE dscGetEEPROM(DSCB board, DWORD address, BYTE* data)
```

Reads 8-bit data from the EEPROM at the specified address. The EEPROM on all AT boards and Emerald-MM-8 contains 256 bytes. On the AT boards, all 256 bytes are addressable. On the Emerald-MM-8, only the lower 128 bytes are addressable. If there is a timeout failure waiting for the EEPROM to respond, the function will return DE\_OPERATION\_TIMED\_OUT.

{% tabs %}
{% tab title="Input Parameters" %}
| Name    | Description                                                                                                     |
| ------- | --------------------------------------------------------------------------------------------------------------- |
| DSCB    | The handle of the board to operate on                                                                           |
| address | Address in the EEPROM to read data from. On AT boards, the range is 0-255. On Emerald-MM-8, the range is 0-127. |
| data    | 8-bit data from the specified address in the EEPROM                                                             |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
