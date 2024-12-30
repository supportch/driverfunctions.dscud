# APPENDIX A: TESTING FTP SERVER

Open any FTP application like Filezilla in development PC and type the following address in Host field. Then enter the QNX username and password and click on Quickconnect.

Host : _ftp: // < IP address of Aries board>_&#x20;

Example:&#x20;

_ftp://10.0.84.71_

Username: diamond

Password : diamond

![Figure 15: FileZilla FTP server screen](broken-reference)

**Note:** To know the IP address assigned to the Aries board, type the following command in terminal as shown in the image below.

_$ifconfig_

![Figure 16: IFCONFIG Command](broken-reference)

Once the IP status is active, take a note of the address to connect to the FTP server applications.

Once the files are successfully transferred check that files by logging into QNX user account.

![Figure 17: FileZilla FTP successful screen](broken-reference)

![Figure 18: FTP in QNX OS Screen](broken-reference)
