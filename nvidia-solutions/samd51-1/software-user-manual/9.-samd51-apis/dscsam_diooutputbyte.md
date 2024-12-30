# DSCSAM\_DIOOutputByte

This function outputs the specified data to the specified port. The data is 8 bits for ports A and 5 bits for port B.

```c
BYTE DSCSAM_DIOOutputByte(BYTE Port, BYTE Data);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name | Description                                                                              |
| ---- | ---------------------------------------------------------------------------------------- |
| Port | <p>0 = A, 1 = B for Elton, Stevie &#x26; Jethro </p><p>0 = A, 1 = B, 2 = C for Ziggy</p> |
| Data | 8 bit value to write to the Port 0 and 5 bit value for Port 1                            |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
