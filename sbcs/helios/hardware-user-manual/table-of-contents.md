# Table of Contents

1. [Important Safe Handling Information ](important-safe-handling-information.md)
2. [Introduction](introduction.md)
3. [Functional Block Diagram](functional-diagram.md)
4. [Board Diagram  ](board-diag.md)
5.  [Connector and Jumper Lists ](connectors-and-jumpers/)&#x20;

    &#x20;5.1 [I/O Connectors ](connectors-and-jumpers/io-connectors.md)

    &#x20;5.2 [Configuration Jumpers](connectors-and-jumpers/configuration-jumpers.md)
6.  [I/O Connectors ](io/)

    &#x20;6.1 [Input Power (J4)](io/ip-power.md)

    &#x20;6.2 [I/O Power (J5) ](io/io-power-j5.md)

    &#x20;6.3 [Panel Power Input (J22) ](io/panel-power-ip-j22.md)

    &#x20;6.4 [Serial Ports (J8)](io/serial-ports-j8.md)

    &#x20;6.5 [PS/2 Mouse and Keyboard (J3)](io/ps-2.md)

    &#x20;6.6 [USB (J15, J16) ](io/usb-j15-j16.md)

    &#x20;6.7 [Ethernet (J11) ](io/ethernet-j11.md)

    &#x20;6.8 [VGA (J10) ](io/vga-j10.md)

    &#x20;6.9 [LVDS LCD Interface (J13, bottom side of board)](io/lvds-lcd-interface-j13.md)

    &#x20;6.10 [LCD Backlight (J9) ](io/lcd-backlight-j9.md)

    &#x20;6.11 [IDE (J12) ](io/ide-j12.md)

    &#x20;6.12 [External Battery (J6) ](io/external-battery-j6.md)

    &#x20;6.13 [Digital I/O (J7) ](io/dio.md)

    &#x20;6.14 [Data Acquisition (J17)](io/daq.md)

    &#x20;6.15 [Miscellaneous (J14)](io/miscellaneous.md)

    &#x20;6.16 [Autocalibration (J19) ](io/auto-calibration.md)

    &#x20;6.17 [FPGA Programming (J20)](io/fpga-j20.md)

    &#x20;6.18 [PC/104 ISA Bus (J1, J2)](io/pc-104-isa-bus-j1-j2.md)
7.  [Configuration Jumpers ](configuration-jumpers/)

    &#x20;7.1 [LCD Backlight Power (J18) ](configuration-jumpers/lcd-backlight-power-j18.md)

    &#x20;7.2 [Data Acquisition Interrupt Configuration (J21)](configuration-jumpers/daq-interrupt-j21.md)&#x20;

    &#x20;7.3 [RS-422/RS-485 Configuration (J25, J26) ](configuration-jumpers/rs-422-rs-485-config-j25-j26.md)
8. [System Resources .](system-resources.md)
9.  [Video Features ](video-features/)

    &#x20;9.1 [CRT ](video-features/video-feature.md)

    &#x20;9.2 [LCD ](video-features/lcd.md)

    &#x20;9.3 [Changing the LCD / CRT Resolution](video-features/changing-lcd-crt-resolution/)&#x20;

    &#x20;       9.3.1 [Modifying the BIOS with a New LCD Resolution ](video-features/changing-lcd-crt-resolution/modifying-the-bios-with-a-new-lcd-resolution.md)

    &#x20;        9.3.2 [Updating the BIOS with SPIFLASH Software](video-features/changing-lcd-crt-resolution/updating-bios-with-spiflash-software.md)&#x20;
10. [Installation and Configuration  ](installation-and-configuration/)

    10.1 [Quick Setup](installation-and-configuration/quick-setup.md)&#x20;

    10.2 [Boot Device Options](installation-and-configuration/boot-device-options.md)
11. [BIOS Functions ](11.bios-functions/)

    11.1 [Entering the BIOS](11.bios-functions/11.1-entering-the-bios.md)&#x20;

    11.2 [Restoring Default BIOS Settings](11.bios-functions/11.2-restoring-default-bios-settings.md)

    11.3 [Setting the Date and Time ](11.bios-functions/11.3-setting-the-date-and-time.md)

    11.4 [Built-In Flash Drive with FreeDOS  ](11.bios-functions/11.4-built-in-flash-drive-with-freedos.md)

    11.5 [ISA Bus IRQ Reservation ](11.bios-functions/11.5-isa-bus-irq-reservation.md)

    11.6 [Blue LED ](11.bios-functions/11.6-blue-led.md)

    11.7[ ISA Bus Speed ](11.bios-functions/11.7-isa-bus-speed.md)

    11.8 [Quiet / Quick Boot / Splash Screen ](11.bios-functions/11.8-quiet-quick-boot-splash-screen.md)

    11.9 [Boot Priority ](11.bios-functions/11.9-boot-priority.md)

    11.10 [System Reset ](11.bios-functions/11.10-system-reset.md)
12. [Serial Ports and System Console](serial-port-and-system-console/)

    12.1 [Overview ](serial-port-and-system-console/12.1-overview.md)

    12.2 [Serial port Configuration](serial-port-and-system-console/12.2-serial-port-configuration.md)&#x20;

    12.3 [Console Redirection to a Serial Port](serial-port-and-system-console/12.3-console-redirection-to-a-serial-port.md)
13. [Data Acquisition Circuit Overview ](13.-data-acquisition-circuit-overview.md)
14. [Data Acquisition I/O Register Map ](daq-register-map/)

    14.1[ Overview ](daq-register-map/14.1-overview.md)

    14.2 [Register Write Functions ](daq-register-map/14.2-register-write-functions.md)

    14.3 [Register Read Functions ](daq-register-map/14.3-register-read-functions.md)

    14.4 [I/O Map Detailed Description ](daq-register-map/14.4-i-o-map-detailed-description-1/)

    &#x20;       14.4.1 [Main Registers](daq-register-map/14.4-i-o-map-detailed-description-1/14.4.2-page-0-counter-timer-control/untitled.md)&#x20;

    &#x20;       14.4.2 [Page 0: Counter/Timer Control ](daq-register-map/14.4-i-o-map-detailed-description-1/14.4.2-page-0-counter-timer-control/)

    &#x20;       14.4.3 [Page 1: AutoCalibration Control ](daq-register-map/14.4-i-o-map-detailed-description-1/14.4.3-page-1-autocalibration-control.md)

    &#x20;       14.4.4 [Page 2 Expanded FIFO and AD/DA Control ](daq-register-map/14.4-i-o-map-detailed-description-1/14.4.4-page-2-expanded-fifo-and-ad-da-control.md)
15. [Analog-to-Digital Input Ranges and Resolution](ad-input-ranges-and-resolution/)&#x20;

    15.1 [Overview ](ad-input-ranges-and-resolution/15.1-overview.md)

    15.2 [Input Range Selection ](ad-input-ranges-and-resolution/15.2-input-range-selection.md)
16. [Performing an A/D Conversion](16.performing-an-a-d-conversion/)&#x20;

    16.1[ Introduction ](16.performing-an-a-d-conversion/16.1-introduction.md)

    16.2 [Select the Input Channel ](16.performing-an-a-d-conversion/16.2-select-the-input-channel.md)

    16.3 [Select the Input Range ](16.performing-an-a-d-conversion/16.3-select-the-input-range.md)

    16.4 [Select the Polarity](16.performing-an-a-d-conversion/16.4-select-the-polarity.md)&#x20;

    16.5 [Wait for Analog Input Circuit to Settle](16.performing-an-a-d-conversion/16.5-wait-for-analog-input-circuit-to-settle.md)

    16.6[ Perform an A/D Conversion on the Current Channel](16.performing-an-a-d-conversion/16.6-perform-an-a-d-conversion-on-the-current-channel.md)

    16.7 [Wait for the Conversion to Finish ](broken-reference)

    16.8[ Read the Data from the Board ](16.performing-an-a-d-conversion/16.8-read-the-data-from-the-board.md)

    16.9 [Convert the Data to Volts or Engineering Units ](16.performing-an-a-d-conversion/16.9-convert-the-data-to-volts-or-engineering-units/)

    &#x20;        16.9.1 [Conversion Formula for Bipolar Input Ranges](16.performing-an-a-d-conversion/16.9-convert-the-data-to-volts-or-engineering-units/16.9.1-conversion-formula-for-bipolar-input-ranges.md)

    &#x20;        16.9.2 [Conversion Formula for Unipolar Input Ranges ](16.performing-an-a-d-conversion/16.9-convert-the-data-to-volts-or-engineering-units/16.9.2-conversion-formula-for-unipolar.md)
17. [A/D Scan, Interrupt and FIFO Operation](17.a-d-scan-interrupt-and-fifo-operation.md)
18. [Digital-to-Analog Output Ranges and Resolution](da-output-ranges-and-resolution/)&#x20;

    18.1 [Description ](da-output-ranges-and-resolution/18.1-description.md)

    18.2[ D/A Resolution ](da-output-ranges-and-resolution/18.2-d-a-resolution.md)

    18.3 [Output Range Selection ](da-output-ranges-and-resolution/18.3-output-range.md)

    18.4 [D/A Conversion Formulas and Tables](da-output-ranges-and-resolution/18.4-d-a-conversion-formulas-and-tables/)

    &#x20;        18.4.1 [D/A Conversion Formulas for Unipolar Output Ranges ](da-output-ranges-and-resolution/18.4-d-a-conversion-formulas-and-tables/18.4.1-d-a-conversion-formulas-for-unipolar-output-ranges.md)

    &#x20;         18.4.2 [D/A Conversion Formulas for Bipolar Output Ranges](da-output-ranges-and-resolution/18.4-d-a-conversion-formulas-and-tables/18.4.2-d-a-conversion-formulas-for-bipolar-output-ranges.md)
19. [Generating an Analog Output ](generating-analog-output/)
20. 19.1 [Set Simultaneous Update Mode and/or DAC Resolution ](generating-analog-output/19.1-set-simultaneous-update-mode-and-or-dac-resolution.md)

    19.2 [Configure the Desired Output Range ](generating-analog-output/19.2-configure-the-desired-output-range.md)

    19.3[ Compute the D/A Code for the Desired Output Voltage](generating-analog-output/19.3-compute-the-d-a-code-for-the-desired-output-voltage.md)

    19.4 [Write the Value to the Selected Output Channel Registers ](generating-analog-output/19.4-write-the-value-to-the-selected-output-channel-registers.md)

    19.5 [Update the D/A ](generating-analog-output/19.5-update-the-d-a.md)
21. [Analog Circuit Calibration ](analog-circuit-calibration.md)
22. [Digital I/O Ports ](digital-io-ports/)

    21.1 [Data Acquisition Circuit Digital I/O Ports ](digital-io-ports/21.1-data-acquisition-circuit-digital-i-o-ports.md)

    21.2 [Vortex Processor Digital I/O Ports ](digital-io-ports/21.2-vortex-processor-digital-i-o-ports.md)

    21.3 [Digital Interrupts](digital-io-ports/21.3-digital-interrupts.md)
23. [Counter/Timer Operation ](counter-timer-operation/)

    22.1 [Counter 0 – A/D Sample Rate Control ](counter-timer-operation/22.1-counter-0-a-d-sample-rate-control.md)

    22.2[ Counter 1 – Counting, Totalizing, and Interrupt Functions ](counter-timer-operation/22.2-counter-1-counting-totalizing-and-interrupt-functions.md)

    22.3 [Command Sequences ](counter-timer-operation/22.3-command-sequences.md)
24. [Watchdog Timer ](23.watchdog-timer.md)
25. [FlashDisk Module ](24.flashdisk-module/)

    24.1 [Overview ](24.flashdisk-module/24.1-overview.md)

    24.2 [IDE Flashdisk Models and Capacities ](24.flashdisk-module/24.2-ide-flashdisk-models-and-capacities.md)

    24.3 [Configuration and Installation ](24.flashdisk-module/24.3-configuration-and-installation.md)

    24.4 [BIOS FlashDisk Configuration ](24.flashdisk-module/24.4-bios-flashdisk-configuration.md)

    24.5 [Using the FlashDisk with Another IDE Drive ](24.flashdisk-module/24.5-using-the-flashdisk-with-another-ide-drive.md)
26. [Mass Storage Accessories](25.-mass-storage-accessories/)&#x20;

    25.1 [ACC-IDEEXT FlashDisk Programmer Board ](25.-mass-storage-accessories/25.1-acc-ideext-flashdisk-programmer-board.md)

    25.2 [ACC-CFEXT CompactFlash Adapter ](25.-mass-storage-accessories/25.2-acc-cfext-compactflash-adapter.md)
27. [Panel I/O Board ](26.panel-i-o-board.md)
28. [I/O Cables](untitled-8.md)
29. [Specifications ](untitled-7/)

    28.1[ Processor Section (All Models) ](untitled-7/28.1-processor-section-all-models.md)

    28.2 [Data Acquisition Section (HLV800-256AV Only) ](untitled-7/28.2-data-acquisition-section-hlv800-256av-and-hlv1000-256av-only.md)
