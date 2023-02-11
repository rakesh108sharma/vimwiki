[[LINUX]]
# bspwm  

## install  
- install: 
    - bspwm 
    - sxhkd (keybindings)
    - dmenu/rofi (launcher menu)
    - nitrogen/feh/hsetroot (wallpaper)
    - picom (compositor)
    - xsetroot
    - arandr/xrandr/lxrandr
    - alacritty (terminal)
    - polybar

```
mkdir -p .config/bspwm
mkdir -p .config/sxhkd

cp /usr/share/doc/bspwm/examples/bspwmrc .config/bspwm/
cp /usr/share/doc/bspwm/examples/sxhkdrc .config/sxhkd/

cp /etx/X11/xinit/xinitrc .xinitrc
```

## configure  
### .xinitrc
```
setxkbmap de &
$HOME/.screenlayout/display.sh
nitrogen --restore &
xsetroot -cursor_name left_ptr
picom -f &
exec bspwm
```  
fix screen resolution with **arandr**  
and save file in $HOME/.screenlayout/display  
and make file executable. 

use nitrogen to set a wallpaper.  


### bspwmrc 
```
sxhkd &

bspc rule -a Chromium desktop='^2'
ex:(bspc rule -a Gimp desktop='^7' state=floating follow=on)  
```  


### sxhkdrc  

