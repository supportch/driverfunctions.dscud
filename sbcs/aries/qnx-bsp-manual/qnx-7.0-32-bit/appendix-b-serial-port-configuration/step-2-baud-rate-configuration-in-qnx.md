# Step 2: Baud Rate configuration in QNX

Login to QNX and set the baud rates using the commands below,

**Setting for 9600 Baud Rates:**

_`# stty baud=9600 < /dev/ser1`_

![Figure 20: 9600 Baud Rate Setup](broken-reference)

**Setting for 115200 Baud Rates:**

_`# stty baud=115200 < /dev/ser1`_

![Figure 21: 115200 Baud Rate Setup](broken-reference)

**Serial Port settings display command:**

_`# stty < /dev/ser1`_
