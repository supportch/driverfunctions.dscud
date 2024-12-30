# DSCGetLastError

Function to get the last known error code and error string.

```c
BYTE DSCGetLastError(ERRPARAMS* errparams);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name      | Description                                                                  |
| --------- | ---------------------------------------------------------------------------- |
| errparams | Pointer to a structure of type ERRPARAMS to fill error code and string info. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
