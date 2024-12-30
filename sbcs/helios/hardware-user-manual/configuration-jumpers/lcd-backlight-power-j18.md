# 7.1 LCD Backlight Power (J18)

Jumper block J18 configures the voltage supply for the LCD backlight. Although the diagrams below show labels on the jumper block, there are no labels on the board. The orientation of the block in the diagrams matches the orientation of the jumper block when the board is rotated so that the PC/104 connector is on the lower edge (facing you). Available options are +5V from the main power supply input or +12V from the auxiliary +12V input. +12V is not used by any circuit on the Helios CPU, so it is not required to provide it on the input power connector. If +12V is needed for the LCD backlight, and the backlight is to be powered via the backlight power connector J9, then +12V must be supplied on the main power input connector along with +5V.

![](broken-reference)

