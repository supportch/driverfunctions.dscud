# 9.1 VIDEO FEATURES

Helios provides a standard CRT port on connector J10. The resolution of the CRT output matches the resolution configured in the BIOS for the LCD. An attached monitor should be able to automatically adapt for many of the available resolutions. If the monitor does not adapt properly, either adjust the monitor settings, change the LCD/CRT resolution in the BIOS (see separate instructions), or use a different monitor.&#x20;

**Note:** The BIOS setup screens and DOS display are always configured for 640x480 resolution, regardless of the display resolution selected in the BIOS. If you configure the BIOS for a different resolution, the display may not look correct when you are in the BIOS setup screens or in DOS. For example, if the screen is set for 1024x768, the BIOS and DOS screens will appear smaller than full screen and will generally be centered in the screen with a blank border around them. If you are using DOS, the optimum CRT resolution is 640x480. This same advice may apply for a text-based Linux environment as well.&#x20;

Diamond Systems cable number 6981178 is used to connect a monitor to connector J10. It provides a standard DB15 female connector for a CRT.

![](broken-reference)

| Signal Name    | Definition                                                            |
| -------------- | --------------------------------------------------------------------- |
| RED            | RED signal (positive, 0.7Vpp into 75 Ohm load)                        |
| Ground         | Ground return for RED, GREEN, and BLUE signals                        |
| GREEN          | GREEN signal (positive, 0.7Vpp into 75 Ohm load)                      |
| BLUE           | BLUE signal (positive, 0.7Vpp into 75 Ohm load)                       |
| DDC-CLOCK/DATA | Signals used for monitor detection (DDC1 specification)               |
| Key            | Pin missing to match key pin in cable to prevent incorrect connection |
