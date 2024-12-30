# 7.6 APPENDIX F: WINDOWS 10 IMAGE RE-FLASHING

If M.2 2230 SATA is corrupted, try the steps given in troubleshooting section to recover the Windows 10 OS.&#x20;

If the Windows 10 OS could not recover, follow this section to re-flash the Windows 10 image. The following files are present in DVD which received along with Athena-IV SDK kit.

### **Files required**&#xD;

* Windows 10 64bit BSP files

&#x20;       ATHENA-IV\_Windows10\_64bit\_BSP\_32GB\_Image folder with following files

![](broken-reference)

* clonezilla-live--2.5.0-25-i586.iso – CloneZilla OS&#x20;
* tuxboot-0.8.3.exe – To make a pen drive CloneZilla OS bootable&#x20;

### **Setup Requirements**&#xD;

* M.2 2230 SATA of 32GB – Target media&#x20;
* Two 8 GB pen drives&#x20;
* First 8 GB pen drive – To have the ATHENA-IV\_Windows10\_64bit\_BSP\_32GB\_Image folder&#x20;
* Second 8 GB pen drive – To have CloneZilla OS bootable&#x20;
* A development PC with windows 7 OS – To make a pen drive as CloneZilla OS bootable&#x20;

### **Make an 8 GB pen drive as CloneZilla OS bootable:**&#xD;

* Connect the 8 GB pen drive to a windows PC &#x20;
* Run tuxboot-0.8.3.exe and it will show the pen drive in the bottom.

![](broken-reference)

* Select disk image and browse “clonezilla-live-2.5.0-25-i586.iso” file and click ok.&#x20;

![](broken-reference)

* It will start copying files as follows&#x20;

![](broken-reference)

* Finally, it will show the following  screen, click exit and now the pen drive is CloneZilla OS bootable

![](broken-reference)

### **Store Windows 10 BSP image to new/corrupted M.2 2230 SATA using CloneZilla OS**&#xD;

* Copy ATHENA-IV\_Windows10\_64bit\_BSP\_32GB\_Image folder to a pen drive&#x20;
* Connect M.2 2230 SATA to Athena-IV board&#x20;
* Connect CloneZilla bootable pen drive to Athena-IV board
* Connect pen drive which has ATHENA-IV\_Windows10\_64bit\_ BSP\_32GB\_Image folder on Athena-IV board
* Power on the board and boot to BIOS setup (by continuously  pressing DEL key during boot up)
* Go to  Boot->Hard disk priorities then choose CloneZilla pen drive as the first  boot device&#x20;
* Press F10 and save.
* It will boot to CloneZilla OS as follows and select first option and press enter

![](broken-reference)

* Choose language

![](broken-reference)

* The default keyboard layout is US keyboard, therefore if you are using US keyboard, just press enter (i.e. use the option "Don't touch keymap")

![](broken-reference)

* Select following option&#x20;

![](broken-reference)

* Attach pen drive which is having Athena-IV Windows 10 image. Select following option&#x20;

![](broken-reference)

* Select following option&#x20;

![](broken-reference)

* Press Enter to continue

&#x20;

![](broken-reference)

* Wait until the pen drive which has ATHENA-IV\_Windows10\_ 64bit\_BSP\_32GB\_Image folder is detected, once it detects then press “Ctrl+C”. (Remove ATHENA-IV\_Windows10\_64bit\_ BSP \_32GB folder contained pen drive and note pen drive name for reference.)&#x20;

![](broken-reference)

* Select the pen drive which has ATHENA-IV\_Windows10\_ 64bit\_BSP\_32GB\_Image folder, the following is an example, so Choose the pen drive correctly &#x20;

![](broken-reference)

* Select following option&#x20;

![](broken-reference)

* Press enter to continue for next step.

![](broken-reference)

* Select following option.

![](broken-reference)

* Select following option.

![](broken-reference)

* Select following option.

![](broken-reference)

* Select the SATA to restore/copy the Windows 10 BSP image&#x20;

![](broken-reference)

* Select following option

![](broken-reference)

* Select following option&#x20;

![](broken-reference)

* Press Enter to continue

![](broken-reference)

* Type “y” to continue.

![](broken-reference)

* Then it will start copying the image to M.2 2230 SATA

![](broken-reference)

![](broken-reference)

* Once Copying is done, press enter to continue.

![](broken-reference)

* Select Power off.

![](broken-reference)

* Now the M.2 2230 SATA is ready to boot to Athena-IV Windows 10.&#x20;













