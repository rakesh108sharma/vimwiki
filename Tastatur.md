[[LINUX]]
# Tastatur

## notes
* /usr/share/X11/xkb/symbols/de
* xev
* xmodmap

## xev
mit xev kann man rausfinden, welchen code eine Taste hat, oder welche Taste
gedrückt wird.  
> z.B.: ```xev -event keyboard```

## xmodmap
mit xmodmap kann man die "map" "mod"ifizieren.  
man kann einzelne Tasten umfunktionieren oder ausschalten.  
```
xmodmap -e 'keycode 49='
xmodmap -e 'keycode 49=dead_circumflex degree'
```

## setxkbmap
- wähle Layout mit `setxkbmap de`  
- man kann auch Tasten ändern wie mit *xmodmap* (soll auch der modernere Weg
  sein).
  z.B: `setxkbmap -option caps:swapescape`  

## Caps_Lock as Escape script
```bash
while true; do  
    # If a terminal is focused and Caps_Lock != Escape -> Bind Caps_Lock to Escape
    if [ "$(ps -p "$(xdotool getwindowfocus getwindowpid)" -o comm=)" = "st" ] \
        && [ "$(xmodmap -pke | grep "Caps_Lock" | grep "66")" ]; then
            xmodmap -e 'clear Lock' -e 'keycode 66 = Escape'
    fi
            
    # If no terminal is focused and Caps_Lock != Caps_Lock -> Bind Caps_Lock to Caps_Lock
    if [ ! "$(ps -p "$(xdotool getwindowfocus getwindowpid)" -o comm=)" = "st" ] \ 
        && [ "$(xmodmap -pke | grep "Escape" | grep "66")" ]; then 
            xmodmap -e 'clear Lock' -e 'keycode 66 = Caps_Lock'
    fi        
done
```  

