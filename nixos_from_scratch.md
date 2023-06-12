[[LINUX]]

# NixOS from scratch  
- check with **lsblk**
- create partitions with **gfdisk**:
    - 1st partition: 500MB, EFI
    - 2nd partition: rest, linux
- create filesystems:
    - `mkfs.vfat -F 32 -n boot /dev/PARTITION_BOOT`
    - `mkfs.ext4 -L LABELNAME /dev/PARTITION_REST`
- mount partitions:
    - `mount /dev/disk/by-label/LABELNAME /mnt`
    - `mkdir /mnt/boot`
    - `mount /dev/disk/by-label/boot /mnt/boot`
- generate config:
    - `nixos-generate-config --root /mnt`
- edit the configuration:
    - `nano /mnt/etc/nixos/configuration.nix`
- start the installation:
    - `nixos-install`
- reboot



