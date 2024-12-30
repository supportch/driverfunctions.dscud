# 9.3.2 Updating the BIOS with SPIFLASH Software

The BIOS image is programmed into the Helios SBC by using the SPIFLASH utility program.

1. Create a DOS bootable mass storage device such as an IDE flashdisk or a USB memory stick.
2. Copy the desired BIOS image file and the SPIFLASH utility program to the boot device.
3. Install the boot device on the Helios board and power it up.
4.  At the DOS prompt, type the following command.  is the name of the BIOS image file. The

    filename must conform to the DOS 8-character naming convention.

    spiflash u   \<filename.rom>&#x20;
5.  SPIFLASH will automatically reprogram the Helios SBC’s BIOS image and provide a progress indicator. The

    program will indicate successful completion of the process, which should take about 10 seconds.
6. Restart the system and press the DEL key to enter the BIOS SETUP utility.
7.  Hit the left arrow key once to go to the tab labeled “Exit.” Select “Load optimal defaults” using the up/down

    arrow keys, and hit Enter to confirm. Then select “Save and Exit,” and hit Enter to confirm.
8. This completes the BIOS process. Reboot the system with the LCD attached to verify proper performance.
