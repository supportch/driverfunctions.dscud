# dscSerialConfig

```
BYTE dscSerialConfig(dscb, DSCSERIALCONFIG *serialconfig)
```

This function will change the serial protocol and store into EEPROM as per request.

{% tabs %}
{% tab title="Input Paramter" %}
<table><thead><tr><th width="164"></th><th></th></tr></thead><tbody><tr><td><strong>Name</strong></td><td><strong>Description</strong></td></tr><tr><td>DSCB</td><td>The handle of the board to operate on</td></tr><tr><td>serialconfig</td><td><p>Int Protocol[] – which is the array, can set the protocol mode in Protocol[0] variable as following below</p><p>0    - RS232,</p><p>1    - RS422,</p><p>2  - RS485</p><p>(Protocol[0] - Athena-IV and Saturn will support</p><p>Protocol[1] - Only Athena-IV is supporting)</p><p> </p><p>Int Action –</p><p>0.  Set Serial port mode.</p><p>1.  Set Serial port mode and update EEPROM</p><p>2.  Read EEPROM</p><p>(Athena-IV &#x26; Saturn will support)</p><p> </p><p>BYTE* eeprom_data - Curent EEPROM setting for serial port registers.(Athena-IV &#x26; Saturn will support)</p><p> </p><p>int Slewrate - To select Slew rate.(Athena-IV &#x26; Saturn will support)</p></td></tr></tbody></table>
{% endtab %}
{% endtabs %}

|                 |
| --------------- |
| Return Value    |
| Error code or 0 |
