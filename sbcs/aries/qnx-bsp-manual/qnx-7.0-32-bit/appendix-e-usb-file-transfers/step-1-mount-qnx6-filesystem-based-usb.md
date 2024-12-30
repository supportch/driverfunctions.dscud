# Step 1: Mount QNX6 Filesystem based USB

We can format the USB in QNX6 filesystem format using mkqnx6fs command and then mount as like below command,

_`# mkqnx6fs /dev/hd1`_

_`# mount -t qnx6 -o sync=none /dev/hd1 /usb`_

![Figure 29: USB QNX Format Commands](broken-reference)
