# Appendix B: Configuration Of FTP Server

The chapter will show the steps to be followed to install FTP server installation in Ubuntu 20.04.2 LTS operating system.

### Step 1: Installing the FTP Server on Ubuntu. 

Switch to root user.&#x20;

&#x20;                     _$ su root_ \
\
&#x20;                     _$ enter the root login password_\
\
&#x20;                     _$ apt-get install vsftpd_

\
Open vsftpd.conf file, the file is present in /etc path. \
\
&#x20;                     _$ vi /etc/vsftpd.conf_ \
\
Edit vsftpd.conf file to enable to upload and download files from the ftp server.\
\
&#x20;                     Uncomment the below mentioned lines in the file. \
\
listen=YES\
\
&#x20;                      anonymous\_enable=YES \
\
&#x20;                      local\_enable=YES&#x20;

&#x20;                      write\_enable=YES

&#x20;                      local\_umask=077 (Changing the mask value)&#x20;

&#x20;                      annon\_upload\_enable=YES&#x20;

&#x20;                      annon\_mkdir\_write\_enable=YES

### Step 2: To Create a directory to upload and download in the FTP server.&#x20;

&#x20;                   _$ setfacl –d –m g::rwx /srv/ftp_ \
\
&#x20;                     _$ setfacl –d –m o::rwx /srv/ftp_ \
\
&#x20;                     _$ mkdir –p /srv/ftp/upload_&#x20;

&#x20;                     _$ mkdir –p /srv/ftp/download_ &#x20;

&#x20;                     _$ chown ftp:ftp /srv/ftp/upload_&#x20;

&#x20;                     _$ chown ftp:ftp /srv/ftp/download_

### Step 3: Testing the FTP Server&#x20;

Open a web browser in development PC or target board or FTP client like Filezilla Type the following in address space.&#x20;

&#x20;                       _**ftp://\<IP address of Saturn board>**_                        _**example ftp://10.0.3.104**_

**Note:** To know the IP address assigned to the Saturn board, type following command in terminal

&#x20;                      _$ifconfig_
