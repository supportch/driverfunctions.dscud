# Step 1: Ethernet Connection in LAN Controller1

Connect the LAN cable in the Ethernet controller1 port and check the IP address using the command ‘ifconfig’. If IP is not assigned then use the dhclient command as below for assigning the IP address.

**Command to startup the connection:**

_`# dhclient –nw wm0`_\


This command will make the Ethernet connection as ‘active’ with its IP as shown in the image below.

![Figure 25: LAN Controller1 Commands with dhclient](broken-reference)

![Figure 26: LAN Controller1 Ping Command](broken-reference)
