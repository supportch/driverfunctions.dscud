# 6.	CUSTOMIZING AND DEPLOYING A RUN-TIME IMAGE

* To customize the Windows 10 image, follow the instructions below. Download Windows Assessment and Deployment Kit for Windows 10 version 1809 LTSC and install in the development machine.
* At an elevated command prompt, locate the Windows Assessment and Deployment Kit (Windows ADK) servicing folder, and type the following command to retrieve the name or index number for the image that you want to modify. For example, create a folder as test in C directory. Inside test folder, create a folder as images and put the install.wim.

&#x20;          **Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim**

* Take the install.wim from the source folder of Windows 10 bootable image.

![](broken-reference)

* Download Windows Assessment and Deployment Kit for Windows 10 version 1809 LTSC from the below mentioned path.

&#x20;       [https://docs.microsoft.com/en-us/windows-hardware/get-   started/adk-install](https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install)

&#x20;    &#x20;
