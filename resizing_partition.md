[[LINUX]]

# resizing partitions  

## needed tools  
- df / lsblk
- mount / umount
- fdisk
- e2fsck
- resite2fs

## procedure  
- find the partition you want to resize:
    - `df -h`  **OR**  `lsblk`
- unmount the wanted partition:
    - `sudo umount MOUNTING-POINT`
- use *fdisk* on the DISK:
    - `sudo fdisk /dev/DISK`
    - `p` for printing the list of partition on the disk
    - write down the **START-Sector** of the wanted partition
    - `d` for deleting the wanted partition
    - `w` for writing the new table
    - `n` for creating a new partition:
        - most things can take the default value, **BUT**
        - START-Sector of new partition **MUST** be the **SAME** as the old partition
    - `w` write
- verify consistency of the new partition:
    - `sudo e2fsck -f /dev/NEW-PARTITION`
    - the check will fail and the program asks you to abort:
        - `no` you want to **continue**
- fix the error:
    - `sudo resize2fs /dev/NEW-PARTITION`
- the END:
    - check again consistency
    - mount partition
    - check size with `df -h`


