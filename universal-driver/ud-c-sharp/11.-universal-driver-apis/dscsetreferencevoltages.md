# dscSetReferenceVoltages()

```c
byte dscSetReferenceVoltages(short board, IntPtr refs);
```

Stores the autocalibration reference voltages in the EEPROM. These voltages are measured on-board and stored in the EEPROM during the factory calibration process. This is a utility function that normally does not need to be called in a user application.

{% tabs %}
{% tab title="Input Parameters" %}
| Name  | Description                                                                                                                                                                                                                                                                                                                                                              |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| board | The handle of the board to operate on                                                                                                                                                                                                                                                                                                                                    |
| refs  | Array containing the reference voltages stored in the EEPROM. These are the voltages from the on-board precision voltage divider circuit that are used for autocalibration. During autocalibration, the driver software will measure the actual reference voltages and calibrate the board until the A/D readings match the stored values. The array size is 8 elements. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
