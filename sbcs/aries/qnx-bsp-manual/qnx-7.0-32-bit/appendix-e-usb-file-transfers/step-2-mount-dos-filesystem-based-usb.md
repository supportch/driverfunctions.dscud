# Step 2: Mount DOS Filesystem based USB

We can mount the USB (FAT filesystem) by the command below and then start transferring the files.

_`# mount –t dos /dev/hd1t12 /tmp/media`_

\
&#xNAN;_`# cd /tmp/media/`_

Here _/tmp/media_ is the USB path we can list out available files in the USB using _‘ls’_ command.

**Note** : USB pendrive filesystem type should be FAT/FAT32.

![Figure 30: USB DOS Format Commands](broken-reference)
