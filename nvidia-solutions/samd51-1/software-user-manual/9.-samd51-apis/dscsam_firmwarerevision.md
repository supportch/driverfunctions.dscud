# DSCSAM\_FirmwareRevision

This function reads the firmware revision ID from SAM.

```c
BYTE DSCSAM_FirmwareRevision(BYTE * Rev_ID);
```

{% tabs %}
{% tab title=" Input Parameters" %}
| Name    | Description                             |
| ------- | --------------------------------------- |
| Rev\_ID | pointer to receive firmware revision ID |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
