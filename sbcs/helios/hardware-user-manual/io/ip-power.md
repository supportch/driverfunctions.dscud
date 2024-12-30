# 6.1 Input Power (J4)

Input power may be supplied using either the input power connector J4, the I/O power connector J5, or directly through the PC/104 bus power pins, if a PC/104 power supply is used with the CPU.&#x20;

The board only requires +5VDC input power to operate. All other required voltages are generated on board. The +12V, -12V, and -5V inputs are provided for convenience and are passed onto the PC/104 bus but are not used by Helios. The +3.3V input is passed through to the LCD connector and may be used to power an attached LCD. Multiple +5V and ground pins are provided for extra current carrying capacity. Each pin is rated at 3A max.&#x20;

For applications requiring less than 3A, the first four pins may be connected to a standard 4-pin miniature PC power connector, or the alternate power I/O connector may be used. For a larger PC/104 stack the total power requirements should be calculated to determine whether additional power input wires are necessary.

![](broken-reference)

Connector type: Standard .1” single row straight pin header with gold flash plating
