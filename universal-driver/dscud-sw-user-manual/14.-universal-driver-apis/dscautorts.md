# dscAutoRTS

```
BYTE dscAutoRTS (dscb, DSCAutoRTS *AutoRTS)
```

This function will enable or disable RTS for RS422 & RS485

{% tabs %}
{% tab title="Input Parameters" %}
<table><thead><tr><th width="150"></th><th></th></tr></thead><tbody><tr><td><strong>Name</strong></td><td><strong>Description</strong></td></tr><tr><td>DSCB</td><td>The handle of the board to operate on</td></tr><tr><td>AutoRTS</td><td><p>Unsigned int DataLength – Data length will be 5-8 and start &#x26; stop bits.</p><p> </p><p>BYTE Enable – 1 enable or 0 disable the RTS. </p><p> </p><p>BYTE Port – which port we are going to use (0 or 1). </p><p>BYTE Pol – polarity of the port to high or low pulse</p><p>(If RTSPOL = 0, the RTSOUT pin is normally low, and the pulse will be high. If RTSPOL = 1, the RTSOUT pin is normally high, and the pulse will be low. In Auto RTS mode, the RTS input signal for a port is ignored).</p><p> </p><p>double baudrate – Baudrate which are using for COM1 &#x26; COM2 (1200 - 256000) (Supports Saturn)</p></td></tr></tbody></table>
{% endtab %}
{% endtabs %}

|                 |
| --------------- |
| Return Value    |
| Error code or 0 |
|                 |
