# DSCSAM\_DIOBitConfig

This function sets the digital I/O bit direction, pull and drive configuration for the selected port bit.

```c
BYTE DSCSAM_DIOBitConfig(BYTE Port, BYTE Bit, BYTE Pull, BYTE Drive, BYTE Dir);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name  | **Description**                                                                                                                         |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Port  | <p>0-1 for port A, B for Elton, Stevie &#x26; Jethro</p><p>0-2 for port A, B, C for Ziggy</p>                                           |
| Bit   | <p>0-7 for port A, 0-4 for port B for Elton, Stevie &#x26; Jethro</p><p>0-7 for port A, 0-4 for port B and 0-7 for port C for Ziggy</p> |
| Pull  | 1 = enabled, 0 = disabled                                                                                                               |
| Drive | 1 = high, 0 = normal                                                                                                                    |
| Dir   | 1 = out, 0 = in                                                                                                                         |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
