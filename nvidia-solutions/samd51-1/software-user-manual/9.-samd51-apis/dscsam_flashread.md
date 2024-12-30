# DSCSAM\_FLASHRead

This function read the data from user specified flash address

```c
BYTE DSCSAM_FLASHRead(int Address, BYTE * Data);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name    | Description                                    |
| ------- | ---------------------------------------------- |
| Address | 0 to 63487                                     |
| Data    | pointer to receive the data from given address |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

[\
](https://app.gitbook.com/@diamondsystems/s/samd51-api-user-manual/9.-samd51-apis/dscsam_fancontrol)
