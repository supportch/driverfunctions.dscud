# Appendix E: File Transfer through minicom

**Step 1: Serial port configuration**

·       First, Become root user and start Minicom in configuration mode with the following command:

$ minicom –s

**Figure 21:  Start minicom**

&#x20;Following window appears

**Figure 22:  minicom configuration**

·       Move on Serial port setup and press enter to continue , the following window appears

**Figure 23:  Serial Port Setup**

·       Type A to change serial device, here /dev/ttyS0 means for serial port 1 and change S0 to S1 or S2 based on the requirement.

·       Type E to change baud rate, here 115200 8N1 means 115200 baud rate, 8 bit, no parity and 1 stop bit.

·      \
Once the setting is done press enter to continue. The following window appears

&#x20;             **Figure 24:  Save setup as dfl**

&#x20;

·       Select save setup as dfl and press enter to save the setup, then press exit to proceed further. It will display initializing modem.

&#x20;

**Step 2: File transfer**

&#x20;

·       Press ctrt+A then Z for Mincom’s various option and the window will appear as follows

**Figure 25:  Minicom Command Summary**

&#x20;

·       Press s to send files , it will show the following window

&#x20; &#x20;

**Figure 26:  Press S to send file**

·       Select any of the file transfer protocol, but in the reception side also same file transfer protocol must be selected. After selecting press enter to continue ,the following window will appear

&#x20;

**Figure 27:  Select file to transfe**

&#x20;

Select the Goto option

&#x20;

**Figure 28:  Select Goto Option**

·       Enter file name like diamond\_file\_sample.txt. If the file is not present in current directory, enter full file path name in the box.

·       The file receiving side must be waiting to receive the file, and then go for the next step.

·       Press enter to send the file.

&#x20;

**Figure 29:  Press enter to send file**

&#x20;

**Figure 30:  Sending files**
