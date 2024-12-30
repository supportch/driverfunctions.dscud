# DSCSAM\_SerialPortConfig

This function configures the serial port mode.

```c
BYTE DSCSAM_SerialPortConfig(BYTE Mode, BYTE Port);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name | Description                                         | Applicable Boards        |
| ---- | --------------------------------------------------- | ------------------------ |
| Mode | <p>0 – RS232, </p><p>1 – RS422,</p><p>2 – RS485</p> | Elton, Stevie and Jethro |
| Port | 0 – Serial Port Pair 1 and 2                        | Elton, Stevie and Jethro |
|      | 1 – Serial Port Pair 3 and 4                        | Elton and Stevie         |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
