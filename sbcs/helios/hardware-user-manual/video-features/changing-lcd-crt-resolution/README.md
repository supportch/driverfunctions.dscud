# 9.3 Changing the LCD / CRT Resolution

The LCD / CRT resolution on Helios is controlled by an “extension” embedded in the BIOS. The extension provides only a single fixed resolution. The extension can be swapped with another one to change the resolution using the instructions below. The available LCD resolutions are shown below. Diamond provides preconfigured BIOS images for each available resolution. The default BIOS loaded on boards delivered by Diamond is 1024x768. In the filenames shown, the letter “A” indicates the revision of the file and may be different. If more than one revision is available, select the highest letter or the one that matches your needs.

![](broken-reference)

There are two methods of updating the LCD resolution:&#x20;

* If you are using the standard BIOS, then you can simply use one of the preconfigured BIOS images for Helios that already contains the desired resolution. Refer to section 9.3.2. You will need to change any custom settings after updating the BIOS.&#x20;
* If you have a BIOS with custom default settings, then you need to modify your existing BIOS image by replacing the LCD BIOS extension with a new one. Refer to section 9.3.1\


