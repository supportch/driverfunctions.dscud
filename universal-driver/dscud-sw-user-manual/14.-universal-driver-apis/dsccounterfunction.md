# dscCounterFunction

```c
BYTE dscCounterFunction(DSCB board, DSCCR *dsccr);
```

This function can be used to program any desired function into a counter, except reading which is done by ARIESCounterRead (). The counters have a set of commands used to configure them. Configuration generally Requires the execution of multiple commands. Each call to this function can execute a single command.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**                                        | **Description**                                                            |
| ----------------------------------------------- | -------------------------------------------------------------------------- |
| DSCB                                            | The handle of the board to operate on                                      |
| [DSCCR ](../15.-structure-definitions/dsccr.md) | The settings for all counters in the structure dsccr; see DSCCR definition |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
