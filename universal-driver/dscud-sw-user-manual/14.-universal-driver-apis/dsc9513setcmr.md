# dsc9513SetCMR

```c
BYTE dsc9513SetCMR(DSCB board, DSCQMMCMR* dscqmm_cmr)
```

Configures the Counter Mode Register for a counter on GPIO-MM-11 or GPIO-MM-12. The Counter Mode Register for a counter must be configured before that counter can be used.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name      | Description                                                            |
| --------- | ---------------------------------------------------------------------- |
| DSCB      | The handle of the board to operate on                                  |
| DSCQMMCMR | Structure containing configuration data for the Counter Mode Register. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
