# DSCSAM\_FLASHWrite

This function writes the data into user specified flash address

```c
BYTE DSCSAM_FLASHWrite(int Address, BYTE Data);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name    | Description                          |
| ------- | ------------------------------------ |
| Address | 0 to 63487                           |
| Data    | 8 bit data to write into the address |
{% endtab %}
{% endtabs %}

| Return Value                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------ |
| <p>Error code or 0.<a href="https://app.gitbook.com/@diamondsystems/s/samd51-api-user-manual/9.-samd51-apis/dscsam_flashread"><br></a></p> |
