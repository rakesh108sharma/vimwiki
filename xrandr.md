[[LINUX]]
# xrandr
setting and creating new screen resolutions

## show all resolutions:
    - `xrandr`

## choose another mode (=resolution):
- select output (HDMI, VGA etc,)
- select a mode (1280x720 etc.)
- `xrandr --output "HDMI-A-0" --mode "1280x720"`

## create a new mode
- decide wich resolution you want and set it up with **cvt**:
    - `cvt 1920 800 60`
- create the new mode in **xrandr** by using the output from **cvt**:
    - `xrandr --newmode "1920x800_60.00"  125.00  1920 2024 2216 2512  800 803 813 831 -hsync +vsync`
- add the new mode to your output:
    - `xrandr --addmode "HDMI-A-0" 1920x800_60.00`

this newmode can now be selected like any other resolution.

