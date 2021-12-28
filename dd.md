[[LINUX]]
# dd
copy disks/partitions over to another drive.  
also create large files.  

## copy system partition
**not complete yet**  

1. first copy the partition to a new partition:
    - `dd if=/dev/drive_a of=/dev/drive_b status=progress`
2. repair and resize:
    1. `e2fsck -f /dev/drive_b`
    2. `resize2fs /dev/drive_b`
3. get new uuid:
    - this is necessary, because the *dd* copied the uuid from *drive_a*
    - `tune2fs -U random /dev/drive_b`
4. `mount /dev/drive_b /mnt`
5. chroot into drive_b:
    - `chroot /mnt bash`
6. change the uuid in /etc/fstab


