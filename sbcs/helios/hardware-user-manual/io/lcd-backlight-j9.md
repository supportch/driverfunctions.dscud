# 6.10 LCD Backlight (J9)

Connector J9 provides the backlight power and control for an optional LCD panel.

![](broken-reference)

The LCD power is jumper selectable for +5V or +12V. See the description for J18. The enable signal controls power to the backlight. It is controlled by digital I/O signal GPIO36. If 12VDC is needed for the LCD, it must be provided either on one of the input power connectors or on the 12V pin (J1, B9) of the PC/104 connector. The board does not generate 12V internally. The brightness control for the LCD backlight has a weak pull-down resistor to ensure maximum brightness when it is not connected externally.

Connector Part Numbers: \
Connector on CPU board:                       Molex 53047-0610 or equivalent \
Mating cable connector:                         Socket: Molex 51021-0600 or equivalent \
Terminals for mating connector:           Molex 50058 / 50079 series or equivalent
