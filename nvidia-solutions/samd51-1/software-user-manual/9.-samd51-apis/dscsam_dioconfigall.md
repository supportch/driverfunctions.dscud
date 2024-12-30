# DSCSAM\_DIOConfigAll

This function sets the digital I/O port directions, pull and drive configurations for all ports at once.

```c
BYTE DSCSAM_DIOConfigAll(BYTE *Pull, BYTE *Drive, BYTE *Dir);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name  | Description                                                                                                                                                                                                    |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pull  | <p>Address of BYTE array of 2 pull configuration values for ports A, B for Elton, Stevie &#x26; Jethro</p><p>Address of BYTE array of 3 pull configuration values for ports A, B and C for Ziggy</p>           |
| Drive | <p>Address of BYTE array of 2 drive configuration values for ports A, B for Elton, Stevie &#x26; Jethro</p><p>Address of BYTE array of 3 drive configuration values for ports A, B and C for Ziggy</p>         |
| Dir   | <p>Address of BYTE array of 2 direction configuration values for ports A, B for Elton, Stevie &#x26; Jethro</p><p>Address of BYTE array of 3 direction configuration values for ports A, B and C for Ziggy</p> |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
