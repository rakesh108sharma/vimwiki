# voidlinux install mit btrfs
this is the btrfs **install**  
later I will take notes of changing an existing install to a better btrfs profil.  

## install
- prepare filesystem:
    - `cfdisk /dev/sdX`
    - create only one partition
    - unless UEFI boot
    - `mkfs.btrfs /dev/sdX1`
- temporary mount on /media:
    - `mount -t btrfs /dev/sdX1 /media`
- make subvolumes:
    - `cd /media`
    - `btrfs subvolume create @`
    - `btrfs su cr @home`
    - `btrfs su cr @snapshots`
    - create more subvolumes if wanted
- now mount all subvolumes on /mnt:
    - `mount -o noatime,compress=zstd,subvol=@ /dev/sdX1 /mnt`
    - `cd /mnt`
    - `mkdir home snapshots`
    - `mount -o noatime,compress=zstd,subvol=@home /dev/sdX1 /mnt/home`
    - `mount -o noatime,compress=zstd,subvol=@snapshots /dev/sdX1 /mnt/snapshots`
- base install:
    - `REPO=https://repo-default.voidlinux.org/current`
    - `ARCH=x86_64`
    - `mkdir -p /mnt/var/db/xbps/keys`
    - `cp /var/db/xbps/keys/* /mnt/var/db/xbps/keys/`
    - `XBPS_ARCH=$ARCH xbps-install -S -r /mnt -R "$REPO" base-system`
- general configuration:
    - `xgenfstab -U /mnt > /mnt/etc/fstab`
    - `xchroot /mnt /bin/bash`
    - `xbps-reconfigure -f glibc-locales`
    - `passwd`
- install grub:
    - `xbps-install -S grub`
    - `grub-install /dev/sda`
- finalization:
    - `xbps-install -S xtools xmirror vim duf htop`
    - `xbps-reconfigure -fa`
    - `exit`
    - `umount -R /mnt`
    - `shutdown -r now`


