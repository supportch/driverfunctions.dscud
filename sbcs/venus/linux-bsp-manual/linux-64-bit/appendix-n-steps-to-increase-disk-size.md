# APPENDIX N: STEPS TO INCREASE DISK SIZE

1\. BSP is created for 64GB Disk. If the BSP is flashed on the Disk has size of more than 64GB then it will not be detected automatically.

2\. Follow below steps one by one to extend the disk size.

3\. Once the OS is booted, Install gparted using below command,

“sudo apt-get install gparted”

4\. Open **Gparted** and follow below steps one by one.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

5\. Unallocated spaces can be added to local partition /dev/sda3 or it can be created as separate partition.

6\. Right click on /dev/sda3 and select Resize/Move.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>



7\. In below window, move the bar or enter the size of New Volume.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

8\. Click Resize and apply changes.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>



9\. Click apply
