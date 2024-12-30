# APPENDIX B: CONFIGURATION OF FTP SERVER

The chapter will show the steps to be followed to install FTP server installation in Ubuntu 20.04.1 LTS operating system.

### **Step 1: Installing the FTP Server on Ubuntu.**

Switch to root user.

$ su root

$ enter the root login password

$ apt-get install vsftpd

Open vsftpd.conf file, the file is present in /etc path.

$ vi  /etc/vsftpd.conf

&#x20;Edit vsftpd.conf file to enable to upload and download files from the ftp server.

Uncomment the below mentioned lines in the file.

listen=YES

&#x20;            anonymous\_enable=YES

&#x20;            local\_enable=YES

&#x20;            write\_enable=YES

&#x20;            local\_umask=077  (Changing the mask value)

&#x20;            annon\_upload\_enable=YES

&#x20;           annon\_mkdir\_write\_enable=YES

### **Step 2: To Create a directory to upload and download in the FTP server.**

$ setfacl –d –m g::rwx  /srv/ftp

$ setfacl –d –m o::rwx   /srv/ftp

$ mkdir –p /srv/ftp/upload

$ mkdir –p /srv/ftp/download

$ chown ftp:ftp /srv/ftp/upload

$ chown ftp:ftp /srv/ftp/download            &#x20;

### **Step 3: Testing the FTP Server**

Open a web browser in development PC or target board or FTP client like Filezilla Type the following in address space.&#x20;

ftp:// example ftp://10.0.3.104

**Note**: To know the IP address assigned to the Gemini board, type following command in terminal

**$ifconfig**
