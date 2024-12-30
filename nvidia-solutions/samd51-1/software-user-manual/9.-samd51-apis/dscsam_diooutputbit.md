# DSCSAM\_DIOOutputBit

This function outputs a single bit to an output port. The other bits remain at their current values.

```c
BYTE DSCSAM_DIOOutputBit(BYTE Port, BYTE Bit, BYTE Value);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name  | Description                                                                                                                                                                                                                                         |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Port  | <p>Port to write bit to: 0 = A, 1 = B for Elton, Stevie &#x26; Jethro</p><p>Port to write bit to: 0 = A, 1 = B, 2 = C for Ziggy</p>                                                                                                                 |
| Bit   | <p>0-7 indicates the bit position in the port A and for port B the value should be 0-4 for Elton , Stevie &#x26; Jethro</p><p>0-7 indicates the bit position in the port A and for port B the value should be 0-4 and 0-7 for port C for Ziggy.</p> |
| Value | 0 or 1                                                                                                                                                                                                                                              |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
