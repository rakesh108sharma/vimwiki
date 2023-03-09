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

## sysctl
edit /etc/sysctl.conf
```
# protect against SYN flood attack
#sudo sysctl net.ipv4.tcp_syncookies=1
#sudo sysctl net.ipv4.tcp_syn_retries=2
#sudo sysctl net.ipv4.tcp_synack_retries=2
#sudo sysctl net.ipv4.tcp_max_syn_backlog=4096

# Protect against IP spoofing
net.ipv4.conf.all.rp_filter=1
net.ipv4.conf.default.rp_filter=1

# Disable packet forwarding
net.ipv4.ip_forward=0
net.ipv4.conf.all.forwarding=0
net.ipv4.conf.default.forwarding=0
net.ipv6.conf.all.forwarding=0
net.ipv6.conf.default.forwarding=0

# Disable logging martian packages
# Otherwise it might cause DOS
net.ipv4.conf.default.log_martians = 0
net.ipv4.conf.all.log_martians = 0

# Disable Redirect Acceptance
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.all.secure_redirects = 0
net.ipv4.conf.default.secure_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
net.ipv6.conf.default.accept_redirects = 0

# reduce swappiness
vm.swappiness=10
```

