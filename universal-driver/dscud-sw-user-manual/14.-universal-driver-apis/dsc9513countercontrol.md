# dsc9513CounterControl

```c
BYTE dsc9513CounterControl(DSCB board, DSCQMMMCC* dscqmm_mcc, BYTE* status)
```

Initiates a Load, Arm, Load & Arm, Disarm, Save, or Disarm & Save command on a group of counters on GPIO-MM-11 or GPIO-MM-12.&#x20;

An Arm command causes the counter to start counting, and a Disarm command causes it to stop. The counter will not count until it receives an Arm command.

The Save command or Disarm and Save command are used to latch the current contents of the counter into the Hold register for reading. If just the Save command is executed, the counter will continue to count; this is equivalent to the Lap button on a stopwatch. After executing one of these commands, use the dsc9513ReadHoldRegister () function to read the latched data.

The Load command or Load and Arm command are used to load the contents of the Load register into the counter before or while arming it. Before executing one of these commands, use the dscSetLoadRegister() function to load the Load register with the desired data.

The function returns the current counter status bytes in the two-byte array status, which primarily indicates the current state of the outputs of all 5 counters in each group. To just read the status bytes, set the action flags to QMM\_ACTION\_NONE.

{% tabs %}
{% tab title=" Input Parameters" %}
| Name      | Description                           |
| --------- | ------------------------------------- |
| DSCB      | The handle of the board to operate on |
| DSCQMMMCC | Data structure for the function       |
| status    | The counter chip status byte:         |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

{% tabs %}
{% tab title="Status Bit Table" %}
| Bit  | 7    | 6    | 5    | 4    | 3    | 2    | 1    | 0    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Name | CMP2 | CMP1 | OUT5 | OUT4 | OUT3 | OUT2 | OUT1 | BPTR |
{% endtab %}
{% endtabs %}

|      |                                                                                                        |
| ---- | ------------------------------------------------------------------------------------------------------ |
| CMPn | Status of the comparators for counters 2 and 1                                                         |
| OUTn | Logic state of the indicated counter output signal                                                     |
| BPTR | Byte pointer internal to the 9513 chip; used by Universal Driver; not relevant to the user application |
