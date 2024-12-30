# DSCSAM\_SerialNumberRead

This function reads the SAM device serial number (128 bit).

```c
BYTE DSCSAM_SerialNumberRead(int* SerialNumber);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name         | Description                          |
| ------------ | ------------------------------------ |
| SerialNumber | pointer to receive the serial number |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
