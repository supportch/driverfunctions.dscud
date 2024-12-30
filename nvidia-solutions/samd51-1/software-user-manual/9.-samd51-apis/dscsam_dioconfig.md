# DSCSAM\_DIOConfig

This function sets the digital I/O port direction, pull and drive configuration for the selected port.

```c
BYTE DSCSAM_DIOConfig(BYTE Port, BYTE Pull, BYTE Drive, BYTE Dir);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name  | Description                                                                                             |
| ----- | ------------------------------------------------------------------------------------------------------- |
| Port  | <p>0-1 for port A, B for Elton, Stevie &#x26; Jethro</p><p>0, 1 and 2 for port A, B and C for Ziggy</p> |
| Pull  | 1 = pull up, 0 = pull down                                                                              |
| Drive | 1 = high, 0 = normal                                                                                    |
| Dir   | 1 = out, 0 = in                                                                                         |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
