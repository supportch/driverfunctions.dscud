# dscDAConvertScan

```c
BYTE dscDAConvertScan(DSCB board, DSCDACS* dscdacs);
```

Performs a set of D/A conversions on multiple target channels.

{% tabs %}
{% tab title="Input Parameters" %}
| **Name**                                           | **Description**                                                     |
| -------------------------------------------------- | ------------------------------------------------------------------- |
| DSCB                                               | The handle of the board to operate on                               |
| [DSCDACS](../15.-structure-definitions/dscdacs.md) | The D/A conversion scan settings to be used; see definition on page |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |

Usage in Helios, DMM32DX and DS-MPE-DAQ0804 boards In Helios SBC and DS-MPE-DAQ0804, the function expects that the user application has called the dscDASetSettings before calling the function. If the user called dscDASetSettings and set the DASIM bit to '1', this function will update all the 4 channels simulataneously. If the DASIM bit is set to '0', the function will start updating channels one at a time.

In DMM32DX implementation of the function, the DASIM usage is implied when this function is used. In DMM32DX, all the 4 channels D/A outputs are updated simultaneously.
