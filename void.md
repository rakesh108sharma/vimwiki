[[LINUX]]
# voidlinux  

## install void linux  
this is an exercise in trying to put together a systematic procedure to install 
void linux (semi automatic)  
[install Void Linux](installVoidLinux.md)  

## grub
Folgende Schritte werden bei der *Erstinstallation* oder beim *repair*
durchgeführt.
### chroot
```
mount --rbind /sys /mnt/sys && mount --make-rslave /mnt/sys
mount --rbind /dev /mnt/dev && mount --make-rslave /mnt/dev
mount --rbind /proc /mnt/proc && mount --make-rslave /mnt/proc

cp /etc/resolv.conf /mnt/etc/

PS1='(chroot) # ' chroot /mnt/ /bin/bash

```
### bios grub
```
xbps-install grub
grub-install /dev/sda
```

### uefi grub
```
xbps-install grub-x86_64-efi
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id="Void"
```

### finalization
Wird nicht immer unbedingt benötigt.  
`xbps-reconfigure -fa`


## xbps package manager

### downgrading a package
#### via xdowngrade
from the *xtools* package  
the package to be downgraded needs to be on disk  

```bash
xdowngrade /var/cache/xbps/pkg-1.0_1.xbps
```  

#### via xbps
First add the package version to your local repository:  
```bash
xbps-rindex -a /var/cache/xbps/pkg-1.0_1.xbps
```  

Then downgrade with xbps-install:  
```bash
xbps-install -R /var/cache/xbps/ -f pkg-1.0_1
```

The -f flag is necessary to force downgrade/re-installation of an already installed package.

### holding packages
To prevent a package from being updated during a system update, use xbps-pkgdb(1):  
```bash
xbps-pkgdb -m hold <package>
```  

### ingnoring a package
Sometimes you may wish to remove a package whose functionality is being provided
by another package, but will be unable to do so due to dependency issues. For
example, you may wish to use doas(1) instead of sudo(8), but will be unable to
remove the sudo package due to it being a dependency of the base-system package.
To remove it, you will need to ignore the sudo package.  

To ignore a package, add an appropriate ignorepkg entry in an xbps.d(5)
configuration file. For example in /etc/xbps.d/sudo.conf:    
`ignorepkg=sudo`  
