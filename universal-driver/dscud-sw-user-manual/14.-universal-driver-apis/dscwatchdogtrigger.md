# dscWatchdogTrigger

```c
BYTE dscWatchdogTrigger(DSCB board);
```

This function retriggers the watchdog timer circuit, causing both counters WD1 and WD2 to be reloaded with their initial values. After a call to dscWatchdogTrigger(), the application has the amount of time specified in WD1 before it must call the function again.

If the watchdog timer has been disabled with a call to dscWatchdogDisable(), than this function will reenable the watchdog timer using the existing watchdog configuration from the last dscWatchdogEnable() call.

This function must not be called before dscWatchdogEnable() is called for the first time, or else undefined results will occur.

In a typical application, dscWatchdogTrigger() is used in a continuous loop to keep retriggering the watchdog timer circuit as evidence that the system is running properly. If the loop ever crashes, or otherwise fails to call dscWatchdogTrigger() in t~~i~~me, the system will reset. The system is configured to automatically restart the application software when it reboots. This way the amount of down time due to a software failure is minimized.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**  |
| -------- | ---------------- |
| DSCB     | The board handle |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
