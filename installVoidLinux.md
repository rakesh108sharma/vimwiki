[[LINUX]]  [void](void.md)  
# install void linux  

## base  
* void-repo-nonfree
* base-devel
* xtools
* rsync
* udevil
* vsv

## user  
* vim
* micro
* lf
* lynx

* bash-completion
* checkbashisms
* highlight
* bat
* mdcat
* mediainfo
* hstr

* mimic
* clipit

* alsa-utils
* mpv
* vlc
* ffmpeg
* gst-plugins-good1
* gst-plugins-bad1
* gst-plugins-ugly1

* flatpak
`flatpak add-remote --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`  

## xorg  
* xorg | xorg-minimal
* picom
* chromium
* firefox

## suckless  
* libX11-devel
* libXinerama-devel
* libXft-devel

change config.mk:
  `X11INC = /usr/include`  
  `X11LIB = /usr/lib`  

```
git clone https://git.suckless.org/dwm
                                  /dmenu
                                  /st
                                  /slstatus
                                  
git clone https://github.com/dudik/herber.git
```


