# DSCSAM\_ADSetSettings

This function configures the A/D channel(current,low & high), scan settings, A/D Trigger, A/D reference, oversampling/averaging, A/D single ended and A/D differential ended.

```c
BYTE DSCSAM_ADSetSettings(DSCSAM_ADSETTINGS* settings);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name       | Description                                                                                                                                                       |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sedi       | 0-1; 0 = single-ended, 1 = differential (Elton, Stevie & Jethro)                                                                                                  |
| Lowch      | low channel, 0-5(Single ended) \[Elton, Stevie, Jethro & Ziggy]                                                                                                   |
|            | low channel, 0-2(Differential ended) \[Elton, Stevie & Jethro]                                                                                                    |
| Highch     | high channel, 0-5(Single ended) \[Elton, Stevie, Jethro & Ziggy]                                                                                                  |
|            | high channel, 0-2(Differential ended) \[Elton, Stevie & Jethro]                                                                                                   |
| Currentch  | channel number 0-5 for current conversion                                                                                                                         |
| ScanEnable | <p>0 = sample,</p><p>1 = scan</p>                                                                                                                                 |
| Adtrig     | <p>00 = software initiated A/D conversion</p><p>01 = external GPIO pin is used to trigger A/D conversion</p>                                                      |
| Adsel      | <p>0 = A/D circuit 0,</p><p>1 = A/D circuit 1</p>                                                                                                                 |
| Adref      | <p>00 = external reference (set to 3.3V)</p><p>01 = internal bandgap reference</p>                                                                                |
| Adtag      | <p>0 = upper 4 bits of 16-bit value = 0000</p><p>1 = upper 4 bits of 16-bit value contain A/D channel number</p>                                                  |
| Adchset    | <p>ADCHSET = 0: Selects channel number for current conversion</p><p>ADCHSET = 1: Selects high/low channel number</p>                                              |
| Adres      | <p>00 = No oversampling, A/D resolution = 12 bits</p><p>01 = A/D resolution = 14 bits</p><p>10 = A/D resolution = 15 bits</p><p>11 = A/D resolution = 16 bits</p> |
| Adsamples  | <p>Number of samples to be accumulated</p><p>1, 2, 4, 8, 16, 32, 64, 128, 256, 512 and 1024</p>                                                                   |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
