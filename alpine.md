[[LINUX]]
# Alpine Linux
in `/etc/apk/repositories` activate the *edge* repository with a tag.
ex: `@testing http://dl-cdn.alpinelinux.org/alpine/edge/testing`

add a package from testing: `apk add package-name@testing`

## install

## post-install
`adduser -h /home/USERNAME -s /bin/ash USERNAME`
`passwd USERNAME`
`adduser USERNAME wheel`

sudo 
    `apk add sudo`
    `echo '%wheel ALL=(ALL) ALL' > /etc/sudoer.d/wheel`
    `adduser USERNAME wheel`
**OR**
doas
    `apk add doas`
    `nano /etc/doas.conf`
        `permit persist :wheel`

utilities:
`apk add util-linux pciutils usbutils coreutils binutils findutils grep iproute2`
`apk add udisks2 udisks2-doc`

## window manager
[dwm](https://wiki.alpinelinux.org/wiki/Dwm)
    `apk add git make gcc g++ libx11-dev libxft-dev libxinerama-dev ncurses`
    `apk add dbus-x11 adwaita-gtk2-theme adwaita-icon-theme ttf-dejavu`
`vi .xinitrc`
    `exec dwm`
`vi .profile`
    `startx`
    **OR**
    `if [[ -z $DISPLAY ]] && [[ $(tty) = /dev/tty1 ]]; then`
        `startx`
    `fi`
    
`adduser USERNAME video`
`adduser USERNAME input`
`adduser USERNAME audio`

`apk add xf86-input-synaptics setxkbmap`

`setup-xorg-base`
`apk add alpine-desktop`
`rc-update add lxdm`
`rc-service lxdm start`

