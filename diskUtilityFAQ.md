# Disk Utility FAQ

Q What to do when you can't format a WD drive?

“MediaKit reports not enough space on device for requested operation”

Suppose the disk is disk4.

IMPORTANT: Select the disk in Disk Utility to find out which disk number it is!

Now let’s force unmount the disk (and all volumes on it):

		diskutil unmountDisk force disk4

And then write zeros to the boot sector:

		sudo dd if=/dev/zero of=/dev/disk4 bs=1024 count=1024

Finally, partition it again:

		diskutil partitionDisk disk4 GPT JHFS+ "XXX" 0g

Where `XXX` is the new disk name.


[Source](https://priyanksharma.com/tech/mediakit-reports-not-enough-space-on-device-for-requested-operation/)
