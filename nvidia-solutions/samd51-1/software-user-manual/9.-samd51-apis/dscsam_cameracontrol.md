# DSCSAM\_CAMERAControl

This function controls the camera specific to Jetson carrier.

```c
BYTE DSCSAM_CAMERAControl(BYTE Value);
```

{% tabs %}
{% tab title="Input Parameters" %}
| Name  | Description                                                                                                                                                                                                                                                                                                      |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Value | <p>1 - 1P2 camera enable</p><p>2 - 1P8 camera enable</p><p>3 - 1P2 camera &#x26; 1P8 camera enable</p><p>4 - 2P8 camera enable</p><p>5 - 1P2 camera &#x26; 2P8 camera enable</p><p>6 - 1P8 camera &#x26; 2P8 camera enable</p><p>7 - 1P2 camera,1P8 camera &#x26; 2P8 camera enable</p><p>0 – All camera OFF</p> |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
