# dscWGBufferSet

```c
BYTE dscWGBufferSet(DSCB board, DWORD address, DSCDACODE value,DWORD channel, BOOL simul)
```

Configures D/A wave form generator D/A output. Sets up the code for D/A output. Gives users control over each output code, the D/A channel intended, and whether it is a simultaneous update or not. Configures D/A wave form generator D/A output. Sets up the code for D/A output. Gives users control over each output code, the D/A channel intended, and whether it is a simultaneous update or not.

{% tabs %}
{% tab title="Input Parameters" %}
| Name      | Description                                                                                                            |
| --------- | ---------------------------------------------------------------------------------------------------------------------- |
| DSCB      | The handle of the board to operate on                                                                                  |
| address   | Address in the buffer to set. This is any where from 0 to (buffer size - 1), i.e. if buffer size is 64 this is 0 to 63 |
| DSCDACODE | D/A code to output                                                                                                     |
| Channel   | D/A channel to output from                                                                                             |
| Simul     | TRUE = enable simultaneous update, FALSE = no simultaneous update                                                      |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
