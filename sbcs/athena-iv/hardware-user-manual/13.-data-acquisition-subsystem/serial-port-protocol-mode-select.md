---
description: This page describes the serial port mode selection with software.
---

# Serial Port Protocol Mode Select

There are 4 serial ports on Athena IV. All the 4 ports support RS-232, RS-422 & RS-485 modes. These protocols can be selected in two different ways:

1. Jumper
2. Software

## 13.8.1 Serial Port Protocol Mode Select with Jumper

The serial port protocols can be selected by changing the jumper positions on JP1. The details have been briefed in the [Section 12.1.1 Select the protocol for the serial ports](../7.-i-o-connectors-jumpers-and-led-refernce-table.md#12-1-1-select-the-protocol-for-the-serial-ports).

## 13.8.2 Serial Port Protocol Mode Select with Software

The serial port protocol modes can also be set with software. The register 15 of page 2 is used for this purpose.

For example, to set serial ports 1 & 2 in RS-422 mode and serial ports 3 & 4 in RS-485 mode, the following code can be written:

```
outp(base+15,0x1D); // SERCFG=1'b1, SC3=1'b1, SC2=1'b1, SC1=1'b0, SC0=1'b1
```

It is important to set bit 4 of the register 15 in page 2 so that the logic is driven on the physical pins of the serial port transceivers. If this bit is not set, then the protocol bits in the register get changed but it doesn't set the desired serial port protocol as the logic is not driven out. SERCFG bit serves as an enable for the protocol mode.

It is also possible to configure the serial ports to particular modes after boot up. This is achieved by writing the particular configuration into the EEPROM.&#x20;

For the same example as above, the following register write sequence can be followed:

```
outp(base+1,0x01); // go to page 1
outp(base+15,0xA5); // unlock the EEPROM to write data
outp(base+12,0x1D); // write EEPROM data
outp(base+13,0xA5); // write EEPROM address; 24 address
                    // location in the EEPROM stores the
                    // serial port control bits
outp(base+14,0x80); // write the data into the EEPROM address

```

To configure the serial ports protocol modes, both jumper & software must not be simultaneously used. All the four serial ports should either be controlled by software or by jumpers but not both.
