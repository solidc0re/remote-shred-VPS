#!/bin/bash

# Acknowledgements: thanks to Kyle Rankin for the idea [https://www.linuxjournal.com/content/remotely-wipe-server]

# Load necessary commands into memory
cp /bin/tee /dev/shm/
cp /bin/echo /dev/shm/
cp /bin/shred /dev/shm/

shutdown_function() {
    /dev/shm/echo 1 | /dev/shm/tee /proc/sys/kernel/sysrq
    /dev/shm/echo o | /dev/shm/tee /proc/sysrq-trigger
}

# Unmount unnecessary filesystems
umount -a

# Shred all non-root partitions
for drive in $(lsblk -ndo NAME | grep -v sda); do
    /dev/shm/shred -n3 -zvfu /dev/$drive
done

# Shred root partition
/dev/shm/shred -n3 -zvfu /dev/sda

# Execute shutdown function
shutdown_function
