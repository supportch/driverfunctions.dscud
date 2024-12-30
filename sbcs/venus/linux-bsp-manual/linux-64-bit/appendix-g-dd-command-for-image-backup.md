# Appendix G: DD command for image Backup

**Step 1: Introduction**

&#x20;Data loss will be costly. At the very least, critical data loss will have a financial impact on companies of all sizes. There are several ways to back up a Linux system.

This section provides practical examples on using dd command to back up the Linux system. dd is a powerful UNIX utility. It can also be used to copy data. Only super user can execute dd command.

&#x20;

**Step 2: Image Backup**

&#x20;

·       Suppose SATADOM disk has Linux OS and need to have a backup of the Linux OS image.

·       Connect the SATA drive in development PC by using SATADOM to USB cable or if you don’t have the cable, boot the target board with some other hard disk (m-SATA port) where the SATADOM drive will be detected as external memory card.

·       Become a root user and enter following command in terminal

·       $fdisk –l&#x20;

·      \
It will appear as follows

&#x20;

**Figure 31:  image backup**

·       From the above window .It is clear that /dev/sdb is the SATADOM drive (64.0GB).

·       Use the following command to take Linux image backup.

&#x20;

$ dd if=/dev/sdb of=Linux\_Backup\_image.img

Where if is input file, of is output file

&#x20;      &#x20;

·       It will take minimum 15 minutes. And the img file will be saved in current directory.

**Step 3: Image Restore**

·       The image restoring medium must have same size as original medium.

·       Insert the restoring medium and it must be formatted in FAT format.

·       Use fdisk –l command to know your restoring medium. Ex /dev/sdb or /dev/sdc

·       Once you found your device .Use the following command to restore the imge

·       Change your directory where the img file saved and run the following command

$ dd if= Linux\_Backup\_image.img of=/dev/sdb

&#x20;

·       It will take minimum 15 minutes and once done, the medium is ready to boot the OS.
