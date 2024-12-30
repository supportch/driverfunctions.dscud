# 9.3.1 Modifying the BIOS with a New LCD Resolution

The BIOS image is modified by using a Windows XP utility called MMTOOL.EXE that can be run on any Windows XP computer.&#x20;

You will need the following items to modify the BIOS image:

1. PC with Windows XP
2. MMTOOL software
3. Existing Helios BIOS image
4. Helios LCD BIOS extension files
5. Bootable device with DOS or FREEDOS, such as an IDE flashdisk or USB memory stick
6. SPIFLASH software

Instructions for MMTOOL software: \
1\. Start the MMTOOL software on the Windows computer. \
2\. Click on the “Load ROM” button. \
3\. Select the desired BIOS image file from the table above and click on the **“Open”** button. The following screen will appear:

![](broken-reference)

4\. Click on the item indicated by the arrow. Make sure the ID, Name, and RunLoc values match what is shown.\
5\. Click on the **“Replace”** tab.\
6\. Click on the “Browse” button and select the BIOS extension file that has the desired LCD resolution, then click“Open” to accept the file and close the dialog box. The BIOS extension files are listed below. Note that theBIOS extension files have an extension of .bin instead of .rom. In the filenames shown, the letter “A” indicatesthe revision of the file and may be different for the actual files.

![](broken-reference)

7\. Click on **“Replace”** to replace the item in the list with the new BIOS extension. The screen will display the updated information.\
8\. If you get an error message “Error – ROM space isn’t enough”, then you have selected an invalid file. Check your selection again or contact Diamond technical support for assistance.\
9\. Click on **“Save ROM as..”**, type in the new filename, and click on OK.\
**The filename must conform to the DOS 8-character naming convention.**

