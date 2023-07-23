[[LINUX]]  

# cloning disks with dd and gparted  

## needed  
- gparted
- dd
- gfdisk
- linux on USB (because you need to work on unmounted partitions)

## procedure  
- if the disk you want to clone is bigger than the target disk, you have to shrink a partition first.
- use gparted to find out which drive needs to be cloned where. ex:
    - source: /dev/sda
    - target: /dev/sdb
- shrink a larger partition, so that the source disk will fit on the target disk:
    - select partition
    - menu -> partition -> resize/move -> reduce size
- if there are partitions *behind* the partition you just shrunk, you have to move them:
    - select partition to move
    - menu -> partition -> resize/move -> free space preceding=0
- apply
- clone disk:
    - `sudo dd if=/dev/SOURCE of=/dev/TARGET bs=1M status=progress`
- trying to use gparted to move partitions might throw an error.
  gpt has a backup partition table at the end of the disk which was not copied if you hat
  to shrink the disk first.
  we need to repair that:
  - `sudo gdisk /dev/TARGET`
  - `x` for expert mode (`?` for help)
  - `e` for reallocating backup partition table at the end
  - `w` for write

you can use gparted now to reclaim unallocated space.
use the same steps to move and then resize the partitions.


