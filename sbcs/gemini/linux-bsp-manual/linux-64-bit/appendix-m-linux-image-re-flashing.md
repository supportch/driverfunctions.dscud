# APPENDIX M: LINUX IMAGE RE-FLASHING

If M.2 2242 is corrupted, try the steps given in trouble shooting section to recover the Linux 20.04.1 LTS 64-bit OS.

If the Linux 20.04.1 LTS 64-bit OS could not recover, follow this section to re-flash the Linux image. The following files are present in DVD which received along with Gemini SDK kit

**Files required**

Linux BSP files

8510893\_A\_BSP\_GEMINI\_LNX\_5.4\_64-BIT\_64GB folder with following files

![](broken-reference)



clonezilla-live-20150805-vivid-i686.iso – CloneZilla OS

tuxboot0.8.3.exe – To make a pen drive CloneZilla OS bootable

**Setup Requirements**

M.2 2242 of 32GB/ More – Target media

Two 8 GB pen drives

First 8 GB pen drive – To have Gemini\_LINUX\_BSP folder

Second 8 GB pen drive – To have CloneZilla OS bootable

A development PC with windows 7 OS – To make a pen drive as CloneZilla OS bootable

**Make an 8 GB pen drive as CloneZilla OS bootable:**

Connect the 8 GB pen drive to a windows PC&#x20;

Run tuxboot 0.8.3 and it will show the pen drive in bottom.

![](broken-reference)

Select disk image and browse “clonezilla-live-20150805-vivid-i686.iso” file and click ok.

![](broken-reference)

It will start copying files as follows

![](broken-reference)

Finally it will show the following screen, click exit and now the pen drive is CloneZilla OS bootable

![](broken-reference)

### Store Linux BSP image to new/corrupted M.2 2242 using CloneZilla OS&#x20;

* Copy 8510893\_A\_BSP\_GEMINI\_LNX\_5.4\_64-BIT\_64GB folder to a pen drive&#x20;
* Connect M.2 2242 to Gemini board&#x20;
* Connect CloneZilla bootable pen drive to Gemini board&#x20;
* Connect pen drive which has 8510893\_A\_BSP\_GEMINI\_LNX\_5.4\_64-BIT\_64GB folder to Gemini board&#x20;
* Power on the board and boot to BIOS setup (by continuously pressing DEL key during boot up)&#x20;
* Go to Boot->Hard disk priorities then choose CloneZilla pen drive as first boot device&#x20;
* Press F4 and save.&#x20;
* It will boot to CloneZilla OS as follows and select first option and press enter

![](broken-reference)

Choose language

![](broken-reference)

The default keyboard layout is US keyboard, therefore if you are using US keyboard, just press enter (i.e. use the option "Don't touch keymap")

![](broken-reference)

Select following option

![](broken-reference)

Select following option

![](broken-reference)

Select following option

![](broken-reference)

Press Enter to continue

![](broken-reference)

Select the pen drive which has 8510893\_A\_BSP\_GEMINI\_LNX\_5.4\_64-BIT\_64GB folder, the following is an example ,so Choose the pen drive correctly

![](broken-reference)

Select following option

![](broken-reference)

Press enter to continue for next step.

Select following option

![](broken-reference)

Select following option

![](broken-reference)

Select following option

![](broken-reference)

Select the M.2 2242 to restore/copy the Linux BSP image

![](broken-reference)

Press Enter to continue

![](broken-reference)

Type “y” to continue&#x20;

Then it will start copying the image to M.2 2242

![](broken-reference)

![](broken-reference)

Once Copying is done , press enter to continue&#x20;

Select Power off

![](broken-reference)

Now the M.2 2242 is ready to boot to Gemini Linux Image Ubuntu-20.04.1 LTS 64-bit OS
