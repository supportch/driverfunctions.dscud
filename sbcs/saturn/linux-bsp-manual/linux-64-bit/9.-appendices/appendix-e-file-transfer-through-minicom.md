# Appendix E: File Transfer Through MINICOM

### Step 1: Serial port configuration

* First, Become root user and start Minicom in configuration mode with the following command:

&#x20;                            _$ minicom –s_

![](broken-reference)

Following window appears

![](broken-reference)

* Move on Serial port setup and press enter to continue , the following window appears

![](broken-reference)

* Type A to change serial device, here /dev/ttyS0 means for serial port 1 and change S0 to S1 or S2 based on the requirement.\

* Type E to change baud rate, here 115200 8N1 means 115200 baud rate, 8 bit, no parity and 1 stop bit.\
  &#x20;
* Once the setting is done press enter to continue. The following window appears

![](broken-reference)

* Select save setup as dfl and press enter to save the setup, then press exit to proceed further. It will display initializing modem.

### Step 2: File transfer

* Press ctrt+A then Z for Mincom’s various option and the window will appear as follows

![](broken-reference)

* Press s to send files , it will show the following window

![](broken-reference)

* Select any of the file transfer protocol, but in the reception side also same file transfer protocol must be selected. After selecting press enter to continue ,the following window will appear

![](broken-reference)

Select the Goto option

![](broken-reference)

* Enter file name like diamond\_file\_sample.txt. If the file is not present in current directory, enter full file path name in the box.
* The file receiving side must be waiting to receive the file, and then go for the next step.
* Press enter to send the file.

![](broken-reference)

![](broken-reference)
