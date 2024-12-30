# 7.2 Data Acquisition Interrupt Configuration (J21)

Jumper block J21 is used to configure the data acquisition circuit interrupt selection and interrupt pull-down resistor on the AV model of Helios. Although the diagrams below show labels on the jumper block, there are no labels on the board. The orientation of the block in the diagrams matches the orientation of the jumper block when the board is rotated so that the PC/104 connector is on the lower edge (facing you).&#x20;

If you will use interrupt-based A/D sampling, select one of the available IRQs, 5 or 6, by installing a jumper in the two pins underneath the desired IRQ level. Select only one IRQ level. The IRQ must also be configured in the BIOS as “Reserved” to make it available to the PC/104 bus. The default setting is IRQ5, and the default BIOS configuration reserves IRQ5 for the PC/104 bus.&#x20;

On the PC/104 bus, interrupt signals are driven high when active and tri-stated when inactive. To drive the inactive line to a valid logic level, a 1KΩ pull-down resistor must be attached to any IRQ that is being used. Since the line is only driven high and never low, this technique allows multiple boards to share the same IRQ, because there is never a conflict from two boards driving the IRQ in opposing logic levels. To make shared interrupts work, the interrupt service routine must check the board’s status register to determine whether the board generated the interrupt, and must be able to pass control to another interrupt routine for the same level if needed.&#x20;

If multiple boards are sharing the same IRQ, only one of them can have the pull-down resistor connected in order to ensure proper loading of the signal. Therefore the pull-down resistor is provided as a jumper-configurable option. If Helios is the only board using the assigned IRQ, then install the jumper for the pull-down resistor. If more than one board is using the same IRQ, then one board should have the pull-down resistor connected, and the other boards should each have their pull-down resistor unconnected. The default setting is jumper installed for pull-down resistor connected.

![](broken-reference)

| Label    | Function                                                             |
| -------- | -------------------------------------------------------------------- |
| IRQ6     | Selects IRQ6 for the data acquisition circuit                        |
| IRQ5     | Selects IRQ5 for the data acquisition circuit                        |
| PULLDOWN | Enables 1KΩ pull-down resistor for the data acquisition IRQ selected |

