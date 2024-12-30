# dscSetCalMux()

```c
byte dscSetCalMux(short board, int on);
```

Turns the calibration multiplexor on or off. The calmux is used only for autocalibration. A user application will only need this function if it is implementing a custom calibration routine. A slight delay of about 10 microseconds occurs when enabling or disabling the calibration multiplexor in order to allow the analog input circuit to settle.

{% tabs %}
{% tab title="Input Parameters" %}
| Name  | Description                           |
| ----- | ------------------------------------- |
| board | The handle of the board to operate on |
| on    | TRUE for on or FALSE for off          |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
