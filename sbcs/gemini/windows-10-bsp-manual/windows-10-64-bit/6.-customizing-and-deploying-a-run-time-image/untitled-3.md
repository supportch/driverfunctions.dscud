# 6.7	Extracting WIM File

**Note:** This step is required only if the .wim file has to be created so that the same image can be used multiple times on different system. Otherwise proceed with the next step.&#x20;

1. Connect the HDD which contains windows 10 and M.2 2242 which contains the Windows 10 customized OS installed to the Gemini board.&#x20;
2. Boot the Gemini board to WinPE bootable pen drive.&#x20;
3. WinPE built in DISM tool can be used to capture the image.&#x20;
4. Use below command to capture the drive of M.2 2242.&#x20;

X:\Windows\System32> DISM.exe /Capture-Image /ImageFile:D: Gemini.wim /CaptureDir:C: /Name: Gemini /Bootable&#x20;

X:\Windows\System32> DISM.exe /Capture-Image /ImageFile:D:\system.wim /CaptureDir:S: /Name: Gemini \_system&#x20;

**NOTE:** /Bootable flag is mandatory, System.wim creation also mandatory.&#x20;

**Elapsed time:** around 5 minutes.&#x20;

Here C: is the Drive letter for M.2 2242 which has the installed Windows 10 customized OS image, Gemini.wim is the file name for the file that will be created (any name with file extension as .wim can be used). D: is the drive letter where we want to store created Gemini.wim file, it will be HDD or Pen drive. X: is the WinPE bootable Drive. S: is system reserved partition.&#x20;

So by now Gemini.wim and system.wim files should be created in D: directory.

5\. Now you are having one 64GB Bootable drive i.e. M.2 2242 1. Keep attached pen drive or HDD which is having Gemini.wim and system.wim. Boot from the bootable WinPE pen drive. Then give the following command.&#x20;

X:\Windows\System32> DISM.exe /Apply-Image /ImageFile:D: Gemini.wim /Index:1 /ApplyDir:W:&#x20;

X:\Windows\System32> DISM.exe /Apply-Image /ImageFile:D:\system.wim /Index:1 /ApplyDir:R:&#x20;

X:\Windows\System32>bcdboot.exe w:\Windows /s R:&#x20;

**Elapsed time:** around 20 minutes. Here W: is the Drive letter for M.2 2242 1 which has 59GB partition and R is 100MB partition of the M.2 2242 1.D drive having the stored Gemini.wim and system.wim file. Elapsed time: around 20 minutes. Where J: is the drive letter for M.2 2242 1.
