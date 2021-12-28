[[LINUX]]
# Xorg


## .xinitrc
[.xinitrc](vfile:/home/maya/.xinitrc)

```
xrandr --output HDMI-A-0 --mode 1280x720 &

~/bin/autostart.sh &

exec qtile
```

## autostart.sh
[autostart](vfile:/home/maya/bin/autostart.sh)
```
#!/bin/bash
#
# wird durch .xinitrc gestartet
#

run () {
    if ! pgrep $1 ;
    then
        $@&
    fi
}

#xrandr --output HDMI-A-0 --mode 1280x720 &
sleep 2

setxkbmap de

xset dpms 1800
xset s 1200

amixer set PCM 100%,100%   # max boost

run pavucontrol-qt &      
xrdb .Xresources &        # nicht wirklich nötig
run urxvtd -q -o -f       # nicht wirklich nötig
run picom -b & 
qterminal &
run darkhttpd ~/wiki/my_wiki/site/ --addr 192.168.1.22 --daemon

sleep 2
run volumeicon &          # könnte direkt in qtile ersetzt werden
run chromium http://192.168.1.22:8080 &

sleep 2
amixer set Master 20%
run wallpapershow.sh &
run mount-devices.sh &

sleep 1
mimic -t "All systems online"
run jupyter-notebook &
run tilda -h -g ~/.config/tilda/config_0 &
run clipit &
run sudo ntpd &
run watch_wiki_and_mkdocs.sh &
```

