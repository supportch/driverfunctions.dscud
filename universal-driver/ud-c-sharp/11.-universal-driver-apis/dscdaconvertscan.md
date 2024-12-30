# dscDAConvertScan()

```c
byte dscDAConvertScan(short board, ref DSCDACS dscdacs);
```

Performs a set of D/A conversions on multiple target channels.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name** | **Description**                                                     |
| -------- | ------------------------------------------------------------------- |
| board    | The handle of the board to operate on                               |
| DSCDACS  | The D/A conversion scan settings to be used; see definition on page |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

