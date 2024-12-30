# dscGetRelayMulti

```c
BYTE dscGetRelayMulti(DSCB board, BYTE relayGroup, BYTE* value)
```

Simultaneously gets the state of multiple relays on the board. A "relay group" is a batch of relays that reside on the same internal board register: Pearl-MM: 2 relay groups consisting of 8 relays each Opal-MM: 1 relay group consisting of 8 relays IR104: 3 relay groups: 2 contain 8 relays, 1 contains 4 relays Diamond-MM-48-AT: 1 relay group consisting of 8 relays

{% tabs %}
{% tab title="Input Parameters" %}
| Name       | Description                                                                                                                                                                                                                                                                                                                              |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DSCB       | The handle of the board to operate on                                                                                                                                                                                                                                                                                                    |
| relayGroup | Selected relay group.                                                                                                                                                                                                                                                                                                                    |
| value      | This is an eight-bit value that will store the current state of each relay in the group as one bit (0 or 1). The least significant bit in the value represents the first relay of the group.Please consult the user manual for your particular product to determine the relationship between the bit value (0 or 1) and the relay state. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
