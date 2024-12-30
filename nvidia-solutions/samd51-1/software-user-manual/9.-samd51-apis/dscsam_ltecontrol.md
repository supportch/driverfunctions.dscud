# DSCSAM\_LTEControl

This function controls the LTE modem specific to Jetson carrier.

```c
BYTE DSCSAM_LTEControl(BYTE Value);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name  | Description                           |
| ----- | ------------------------------------- |
| Value | <p>1 = enable, </p><p>0 = disable</p> |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
