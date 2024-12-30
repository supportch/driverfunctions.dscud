# 7.6	Appendix F: Windows 10 Image Re-flashing

If M.2 2242 is corrupted, try the steps given in troubleshooting section to recover the Windows 10 OS.

If the Windows 10 OS could not recover, follow this section to re-flash the Windows 10 image. The following files are present in DVD which received along with Gemini SDK kit.

**Files required**

* Windows 10 64bit BSP files

8510896\_A\_BSP\_Gemini\_WIN10\_64-BIT\_64GB Image folder with following files

![](broken-reference)

* clonezilla-live--2.5.0-25-i586.iso – CloneZilla OS
* tuxboot-0.8.3.exe – To make a pen drive CloneZilla OS bootable

**Setup Requirements**

* M.2 2242 of 64GB – Target media
* Two 8 GB pen drives
* First 8 GB pen drive – To have the 8510896\_A\_BSP\_Gemini\_WIN10\_64-BIT\_64GB Image folder
* Second 8 GB pen drive – To have CloneZilla OS bootable
* A development PC with windows 7 OS – To make a pen drive as CloneZilla OS bootable

**Make an 8 GB pen drive as CloneZilla OS bootable:**

* Connect the 8 GB pen drive to a windows PC&#x20;
* Run tuxboot-0.8.3.exe and it will show the pen drive in the bottom.

![](broken-reference)

* Select disk image and browse “clonezilla-live-2.5.0-25-i586.iso” file and click ok.

![](broken-reference)

* It will start copying files as follows

![](broken-reference)

* Finally, it will show the following  screen, click exit and now the pen drive is CloneZilla OS bootable

![](broken-reference)

**Store Windows 10 BSP image to new/corrupted M.2 2242** **using CloneZilla OS**

* Copy 8510896\_A\_BSP\_Gemini\_WIN10\_64-BIT\_64GB Image folder to a pen drive
* Connect M.2 2242 to Gemini board
* Connect CloneZilla bootable pen drive to Gemini board
* Connect pen drive which has 8510896\_A\_BSP\_Gemini\_WIN10\_64-BIT\_64GB Image folder on Gemini board
* Power on the board and boot to BIOS setup (by continuously  pressing DEL key during boot up)
* Go to  Boot->Hard disk priorities then choose CloneZilla pen drive as the first  boot device
* Press F10 and save.
* It will boot to CloneZilla OS as follows and select first option and press enter

![](broken-reference)

* Choose language

![](broken-reference)

* The default keyboard layout is US keyboard, therefore if you are using US keyboard, just press enter (i.e. use the option "Don't touch keymap")

![](broken-reference)

* Select following option

![](broken-reference)

* Attach pen drive which is having Gemini Windows 10 image. Select following option

![](broken-reference)

* Select following option

![](broken-reference)

* Press Enter to continue

![](broken-reference)

* Wait until the pen drive which has 8510896\_A\_BSP\_Gemini\_WIN10\_64-BIT\_64GB Image folder is detected, once it detects then press “Ctrl+C”. (Remove 8510896\_A\_BSP\_Gemini\_WIN10\_64-BIT\_64GB folder contained pen drive and note pen drive name for reference.)

![](broken-reference)

* Select the pen drive which has 8510896\_A\_BSP\_Gemini\_WIN10\_64-BIT\_64GB Image folder, the following is an example, so Choose the pen drive correctl&#x79;**.**

![](broken-reference)

* Select following option

![](broken-reference)

* Press enter to continue for next step.

![](broken-reference)

* Select following option.

![](broken-reference)

* Select following option

![](broken-reference)

* Select following option

![](broken-reference)

* Select the SATA to restore/copy the Windows 10 BSP image

![](broken-reference)

* Select following option.

![](broken-reference)

* Select following option.

![](broken-reference)

* Press Enter to continue

![](broken-reference)

* Then it will start copying the image to M.2 2242.

![](broken-reference)

![](broken-reference)

* Now the M.2 2242 is ready to boot to Gemini Windows 10.