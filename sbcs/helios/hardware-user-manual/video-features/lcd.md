# 9.2 LCD

There are two common types of LCD signaling used in embedded computers: LVDS and TTL. The LCD output on Helios uses the more popular LVDS (low-voltage differential signaling) format. If you are planning to use a TTL LCD with Helios, you will need to use a small adapter board that converts LVDS to TTL. Many such boards are available from suppliers. The LCD used with Helios must match the programmed resolution and scan rate in the Helios BIOS. These settings can be changed with a software utility provided with the board (see below). Helios provides 18-bit LVDS output, so the LCD selected must work with 18-bit data. As opposed to CRTs, there is no standard LCD connector type or format. Each LCD manufacturer has its own standards, and there are also different specifications such as the number of data bits used in the video signal. You will need to create your own LCD cable to connect from the LCD connector on Helios to the input connector on your LCD. For assistance with signal definitions or wiring requirements, contact the LCD maker or Diamond technical support. Diamond offers cable no. 6981206 with the correct connector type and pinout to match the LCD connector on Helios. The other end may need to be changed to work with your LCD. Connector J13 is used to connect an LVDS LCD to Helios:

![](broken-reference)

If needed, the LCD backlight can be connected to connector J9:

![](broken-reference)

The backlight power is jumper-selectable between +5V and +12V using jumper block J18. If 12VDC is needed for the LCD, it must be provided either on one of the input power connectors or on the 12V pin (J1, B9) of the PC/104 connector. The board does not generate 12V internally.&#x20;

**WARNING**: Be sure the proper voltage is configured BEFORE connecting the cable to your backlight inverter, or it could be damaged. The brightness control for the LCD backlight has a weak pull-down resistor to ensure maximum brightness when it is not connected externally. Diamond offers cable number 6981207 with the correct connector type and pinout to match the backlight power connector on Helios. The other end may need to be changed to work with your LCD backlight inverter.

The enable signal on J9 controls power to the backlight. It is controlled by Helios GPIO signal Port 3 Bit 6. The LCD display can also be enabled or disabled by using GPIO signal Port 3 Bit 5. To control these settings in software, do the following:

1.  Set GPIO direction control register to output:

    outp(0x9B, 3);                                         // sets bits 1 and 0 of GPIO port 3 to output
2.  Set bit 5 of port 3 to 1 to enable or 0 to disable the LCD display. Default setting is enabled.

    outp(0x7B, inp(0x7B) | 0x20);                            // Port 3 bit 5 = 1 for LCD enable

    outp(0x7B, inp(0x7B) & 0xDF);                         // Port 3 bit 5 = 0 for LCD disable
3.  Set bit 6 of port 3 to 1 to enable or 0 to disable the backlight. Default setting is enabled.

    outp(0x7B, inp(0x7B) | 0x40);                          // Port 3 bit 6 = 1 for backlight enable

    outp(0x7B, inp(0x7B) & 0xBF);                        // Port 3 bit 6 = 0 for backlight disable



The LCD backlight can also be configured in the BIOS. Select Chipset, then South Bridge Configuration menu.

The backlight can be enabled or disabled, and its brightness can be set to min or max.
