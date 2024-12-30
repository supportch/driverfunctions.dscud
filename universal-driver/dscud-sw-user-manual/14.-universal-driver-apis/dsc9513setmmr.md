# dsc9513SetMMR

```c
BYTE dsc9513SetMMR(DSCB board, DSCQMMMMR* dscqmm_mmr)
```

Sets the configuration for the Master Mode Register on the 9513 counter/timer chip on GPIO-MM-11 or GPIO-MM12. The Master Mode Register must be configured before any counter on the chip can be used. See the definition of the data type DSCQMMMMR for information on the parameters required. Each 9513 has its own Master Mode Register, i.e. on GPIO-11 with 2 chips, the function must be called once for each chip.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name        | Description                                                          |
| ----------- | -------------------------------------------------------------------- |
| DSCB        | The handle of the board to operate on                                |
| dscqmm\_mmr | Structure containing configuration data for the Master Mode Register |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
