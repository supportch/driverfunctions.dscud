# Appendix C: Configuration Of HTTP Server

The chapter will show the steps to be followed to install Http server installation in Ubuntu 20.04.2 live operating system.

### Step 1: Installing the HTTP Web Server on Ubuntu.&#x20;

Open the terminal. Switch to root user.&#x20;

&#x20;                            _$ su root_&#x20;

&#x20;                            _$ enter the root login password_&#x20;

Type the command.\
\
&#x20;                            _$ apt-get install apache2_

### Step 2: Create and serve our own webpages to user

Copy the desired html files to the following directory. \
\
&#x20;                             _$ cp example.html /var/www/html/_

For Example if user wants to view Diamond system webpage. Copy the Diamond system html page to the above mentioned directory.\
\
&#x20;          _$ cp Diamond.html /var/www/html/_&#x20;

### Step 3: Testing the HTTP Server

To confirm HTTP server works properly, type the followings in web browser address space.

&#x20;                             _http://\<IP address of Saturn Board>  example_ [_http://10.0.0.1_](http://10.0.0.1)

A window with a message “It Works !”appears.

![](broken-reference)

To view copied desired html files in web browser, example to view Diamond webpage, type the followings in web browser address space.

&#x20;                    _http://\<ipaddress of target board/ Diamond.html > (ex:_ [_http://10.0.0.1/_](http://10.0.0.1/) _Diamond.html)_

**Note:** To know the IP address assigned to the Saturn board, type following command in terminal

&#x20;                                                                        _$ifconfig_
