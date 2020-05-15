# attach a disk file into loop device file
losetup -f -o $[2048*512] sda.img