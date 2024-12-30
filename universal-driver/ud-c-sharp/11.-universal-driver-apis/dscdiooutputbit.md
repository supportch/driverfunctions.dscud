# dscDIOOutputBit()

```c
byte dscDIOOutputBit(short board, byte port, byte bit, byte digital_val);
```

Sets the specified digital output bit of the specified port to the specified value (1 or 0) while leaving the other bits in their present states.

Some boards (Diamond-MM, Diamond-MM-AT, Diamond-MM-16-AT, Opal-MM, Pearl-MM, Quartz-MM) do not have readback capability on the digital output ports. Therefore the driver maintains its own history of the last-written values to these ports, so that it can correctly modify only the bit of interest. In order for this function to work correctly, the driver must always know the present state of the digital output bits. This can only happen if you always use the driver for digital output operations. If you mix driver calls with direct I/O to the digital output ports, the bit operations can fail, since the driver will have no record of what your program has done directly.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name**     | **Description**                                        |
| ------------ | ------------------------------------------------------ |
| board        | The handle of the board to operate on                  |
| Port         | Selected output port                                   |
| Bit          | Bit location (0-7) to write on the selected input port |
| digital\_val | Value to write to the bit; 1 or 0                      |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
