# DSCSAM\_DIOInputByte

This function reads in the data from the specified port and returns it in the location specified by the pointer to data.

```c
BYTE DSCSAM_DIOInputByte(BYTE Port, BYTE* Data);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name | Description                                                                             |
| ---- | --------------------------------------------------------------------------------------- |
| Port | <p>0 = A, 1 = B for Elton, Stevie &#x26; Jethro</p><p>0 = A, 1 = B, 2 = C for Ziggy</p> |
| Data | pointer to receive the data read from the port                                          |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
