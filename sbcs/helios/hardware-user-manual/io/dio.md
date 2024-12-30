# 6.13 Digital I/O (J7)

Connector J7 provides 16 digital I/O lines from the Vortex CPU. These lines are buffered and have ESD protection to protect the CPU from potential damage. The buffers enable the direction to be programmed in 8-bit groups, using two additional GPIO lines from the Vortex processor. The direction may be set in the BIOS or by programming the CPU I/O control registers.

![](broken-reference)

| Signal   | Definition                   |
| -------- | ---------------------------- |
| DIO D7-0 | GPIO port 0 from Vortex CPU  |
| DIO E7-0 | GPIO port 1 from Vortex CPU  |
| +5V      | Connected to main +5V supply |
| Ground   | Digital ground               |

**Connector type**: Standard 2mm dual row straight pin header with gold flash plating
