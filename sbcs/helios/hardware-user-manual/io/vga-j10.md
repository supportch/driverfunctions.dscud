# 6.8 VGA (J10)

Connector J10 is used to connect a VGA monitor. Although the DDC serial detection pins are present, a 5V power supply is not provided, and the legacy “Monitor ID” pins are also not used.

![](broken-reference)

| Signal Name    | Definition                                                            |
| -------------- | --------------------------------------------------------------------- |
| RED            | RED signal (positive, 0.7Vpp into 75 Ohm load)                        |
| Ground         | Ground return for RED, GREEN, and BLUE signals                        |
| GREEN          | GREEN signal (positive, 0.7Vpp into 75 Ohm load)                      |
| BLUE           | BLUE signal (positive, 0.7Vpp into 75 Ohm load)                       |
| DDC-CLOCK/DATA | Signals used for monitor detection (DDC1 specification)               |
| Key            | Pin missing to match key pin in cable to prevent incorrect connection |

**Connector type**: Standard 2mm dual row straight pin header with gold flash plating
