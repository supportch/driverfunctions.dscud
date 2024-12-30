# dscADSample()

```csharp
byte dscADSample(short board, ref short sample);
```

Performs a single A/D conversion on the currently selected channel. The function first waits for the board to be ready for a conversion. It then starts the conversion and waits for it to finish before reading data from the board. A built-in timer is used to check for board failure. If the timer times out before the conversion completes, the board returns the error code.

{% tabs %}
{% tab title=" Input Parameters" %}
| **Name** | **Description**                                                                                            |
| -------- | ---------------------------------------------------------------------------------------------------------- |
| board    | The handle of the board to operate on                                                                      |
| sample   | The sample resulting from the A/D conversion; the range of return values depends on the type of A/D board. |
{% endtab %}
{% endtabs %}

| Return Value     |
| ---------------- |
| Error code or 0. |
