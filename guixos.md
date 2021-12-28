[[LINUX]] [[LISP]]
# guix OS
good [video](https://www.youtube.com/watch?v=oSy-TmoxG_Y)
nongnu [website](https://gitlab.com/nonguix/nonguix)

## download installer
[installer](https://guix.gnu.org/en/download/)

- check authentity:
`wget https://ftp.gnu.org/gnu/guix/guix-system-install-1.3.0.x86_64-linux.iso.sig`
`gpg --verify guix-system-install-1.3.0.x86_64-linux.iso.sig`

- copy to USB:
`dd if=guix-system-install-1.3.0.x86_64-linux.iso of=/dev/sdX status=progress`
`sync`

## prepare hard drive
best to wipe disk beforehand and create one only partition

## install
use the graphical installer up to *configuration file* 
- locale language
- locale location
- timezone
- keyboard layout
- hostname
- internet access
- substitute server discovery **ENABLE**
- root password (does not rally matter because I'll use a different approach)
- create USER
- desktop environment (better to install a mainstream DE..will pull all
  necessary package)
- services (Mozilla + SSH)
- partitioning method (entire disk)
- **STOP** using graphical UI
- **Ctrl+Alt+F3**

continue in the terminal
- `herd start cow-store /mnt`
- `cp /etc/channels.scm /mnt/etc`
- `chmod +w /mnt/etc/channels.scm`
- edit `/mnt/etc/config.scm` with emacs:
    - change `(use-modules (gsu))` to `(use-modules (gsu) (nongnu packages linux))`
    - after `(operating-system` add on the next line:
        - `(kernel linux)`
        - `(firmware (list linux-firmware))` 
        - save&exit `ctrl-x ctrl-s` + `crtl-x ctrl-c`
- start installation process:
    - `quix time-machine -C /mnt/etc/channels.scm -- system init /mnt/etc/config.scm /mnt`
- `reboot`

should the installation hang you can stop it with
`ctrl-c` and then start the last command again

## first update
**Before** entering the new system with the login-manager I have to switch to
another tty with `ctrl-alt-F5`

set passwords for root and user:
`passwd`
`passwd USER`
`exit`
`ctrl-alt-F7`

now login.
```
mkdir -p ~/.config/guix
cp /etc/channels.scm ~/.config/guix/
cp /etc/config.scm ~/.config/guix/system.scm
```

edit `~/.config/guix/channels.scm`
delete all lines which say `(commit` till the end

`guix pull`
`sudo -E guix system reconfigure ~/.config/guix/system.scm`

