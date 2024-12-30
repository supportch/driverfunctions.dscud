# 10.2 Boot Device Options

Helios can boot to an IDE device, a USB device, or the on-board 2MB virtual floppy drive. Helios has a single IDE channel that can support up to two devices simultaneously (Master and Slave). IDE devices connect to J12, which is a 44-pin, laptop style IDE connector. This connector has pin 20 cut to match the key pin on Diamond cable number 6981004.&#x20;

**WARNING: It is possible to destroy the Helios SBC by connecting an IDE cable incorrectly (reverse orientation or offset from correct position). Always used keyed cables to avoid connection errors.**&#x20;

The Boot device selection and priority are configured in the BIOS Boot menu. See Chapter 11 for detailed BIOS instructions. Only devices which are currently attached to the SBC will appear in the list of options. Therefore if you want to select a hard drive or USB device as the boot device, you must connect it to the SBC first, then boot up and enter the BIOS, then select it as a boot device.

* Install an IDE flashdisk directly on the IDE connector J12.&#x20;
* Connect a laptop IDE hard drive directly to J12 through a 44-pin ribbon cable such as Diamond Systems cable 6981004.&#x20;
* Use cable 6981004 to connect an IDE flashdisk programmer board to J12. You can then install a flashdisk on the programmer board and connect another 40-pin or 44-pin IDE compatible device to the programmer board. Note that the 44-pin cable will provide +5V power from the SBC to the IDE device, but the 40 pin cable does not carry +5V, so you will need to provide power separately. You can use cable 6981006, attached to J5 on Helios, to provide power from the board to 40-pin devices.&#x20;
* Attach a bootable USB device to one of the USB ports with USB cable number 6981082.&#x20;
* Attach no external storage device to Helios. The system will boot to the FreeDOS installed on the onboard virtual floppy drive, as long as it is enabled in the BIOS.

