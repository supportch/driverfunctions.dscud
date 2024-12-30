# DSCSAM\_WLANControl

This function controls the minicard WLAN specific to Jetson carrier.

```c
BYTE DSCSAM_WLANControl(BYTE Value);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name  | Description                           |
| ----- | ------------------------------------- |
| Value | <p>1 = enable, </p><p>0 = disable</p> |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
