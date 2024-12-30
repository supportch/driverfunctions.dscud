# 6.15 Miscellaneous (J14)

Connector J14 provides access to common miscellaneous signals used in a PC application.

![](broken-reference)

| Signal             | Definition                                                                                                                                                                         |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Speaker            | The signal on this pin is referenced to +5V Out. Connect a speaker between this pin and +5V Out.                                                                                   |
| IDE Drive LED      | Referenced to +5V Out. Does not require a series resistor. Connect LED directly between this pin and +5V Out.                                                                      |
| Power LED          | Referenced to +5V Out. Does not require a series resistor. Connect LED directly between this pin and +5V Out.                                                                      |
| Reset-             | Connection between this pin and Ground will generate a Reset condition.                                                                                                            |
| LCD Backlight Ctrl | User provided brightness control for the LCD backlight; 0V = max, 5V = min. This signal has a pull-down resistor to ensure maximum brightness when it is not connected externally. |
| Reserved           | Not connected, reserved for future use.                                                                                                                                            |

**Connector type**: Standard 2mm dual row straight pin header with gold flash plating
