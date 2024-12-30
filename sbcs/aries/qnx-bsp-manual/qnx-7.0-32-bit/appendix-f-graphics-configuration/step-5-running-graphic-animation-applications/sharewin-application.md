# ShareWin Application

Run the command “./sharewin” in the putty terminal. These are the graphics packages added in QNX 7.0 and its working properly.

This application won’t allow arguments hence it can be executed without arguments and it will be running application on the first connected device by default.

![Figure 43: ShareWin View in QNX](broken-reference)

For changing the display devices in the configuration file, again copy the file through USB change the display numbers in host machine and replace it in “/lib/graphics.conf” in QNX machine. Then run the below command as shown in the image below.

_`# slay screen`_

_`# cd /etc/`_

_`# ./start-screen.sh`_

![Figure 44: Screen Restart](broken-reference)

Then run the graphic applications as we do it in the above steps.
