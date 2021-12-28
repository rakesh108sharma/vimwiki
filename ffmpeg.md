[[LINUX]]
# ffmpeg

## convert files

### convert video format
`ffmpeg inputfile.mp4 outputfile.mkv`  
just mention the outputfile with the wanted filetype; e.g mp3, mp4, mkv, ogg
etc.  

### compress video
`ffmpeg -i INPUTFILE -vcodec libx265 -crf 28 OUTPUTFILE`
**OR**
`ffmpeg -i INPUTFILE.mp4 -c:v libx264 -crf 22 -c:a copy OUTPUTFILE.mp4`
-crf            0-64 (higher = more compression)
**OR**
`ffmpeg -i INPUTFILE.mp4 -c:v libx264 -b:v 1M OUTPUTFILE.mp4`
-b              average bitrate
**OR with vp9 compression**
`ffmpeg -i INPUTFILE.mp4 -c:v libvpx-vp9 -crf 22 -b:v 0 OUTPUTFILE.webm`

### compress audio
`ffmpeg -i INPUTFILE.mp3 -c:a aac -b:a 128k OUTPUTFILE.m4a`
aac needs m4a container
**OR**
`ffmpeg -i INPUTFILE.mp3 -b:a 98k OUTPUTFILE.mp3`
**OR with libvorbis**
`ffmpeg -i INPUTFILE.mp3 -c:a libvorbis -vbr 2 OUTPUTFILE.ogg`
libvorbis needs ogg container
-vbr      not always needed


### remove audio/video
`ffmpeg -i INPUTFILE -c copy -an OUTPUTFILE`
-vn      remove video

### extract video
in **remove audio** a copy of the inputfile is made *without* the audio stream.
**here** the video stream is extracted from the original file.
- first check which *stream* to extract:
    - `ffmpeg -i INPUTFILE`
- also check what *codec* that stream is (ex. webm)
`ffmpeg -i INPUTFILE -map 0:0 -codec copy OUTPUTFILE.webm`

### extract audio
again check which *stream* AND which *codec* 
`ffmpeg -i INPUTFILE -map 0:1 -codec copy OUTPUTFILE.aac`


### resize video
- the dimensions need to be divisable by 2
`ffmpeg -i INPUTFILE -s 640x360 -c:a copy OUTPUTFILE`
**OR**
`ffmpeg -i INPUTFILE -filter:v scale=-1:720 -c:a copy OUTPUTFILE`
-filter:v       video
scale=-1:720    720,1080,480,360,240 (needs only height .. will keep the ratio)

**if the size is not divisible by 2:**
`ffmpeg -i INPUTFILE -filter:v scale="trunc(oh*a/2)*2:720" -c:a copy OUTPUTFILE`

### make GIF
easiest but slow and big and bad without control:
`ffmpeg -i INPUTFILE OUTPUTFILE.gif`
**BETTER**
```
ffmpeg -i INPUTFILE -vf
"fps=10,scale=trunc(oh*a/2)*2:240:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse"
-loop 0 OUTPUTFILE.gif
```

### get a thumbnail
`ffmpeg -i INPUTFILE -ss 5 -vframes 1 OUTPUT.png`
-ss            at what time (seconds) the image should be taken
-vframes 1     only 1 frame is needed
-s             size can be added too (360x240)

**getting more images**
`ffmpeg -i INPUTFILE -vf fps=1/2 OUTPUTFILE%03d.jpg`
fps 1/2      1 pic every 2 seconds
    2        2 pic every 1 second
    1/8      1 pic every 8 seconds
%03d         3 decimals


### filters
#### convert into black&white
`ffmpeg -i INPUTFILE -vf hue=s=0 OUTPUTFILE`
-vf             video filter
hue=s=0         hue and saturation is 0
**OR**
`ffmpeg -i INPUTFILE -vf format=gray OUTPUTFILE`

#### invert
`ffmpeg -i INPUTFILE -vf negate OUTPUTFILE`

#### changing brightness
`ffmpeg -i INPUTFILE -vf eq=brightness=2 OUTPUTFILE`
brightness=2     doubble the brightness
                 1 is default

#### sharpen a video
`ffmpeg -i INPUTFILE -vf unsharpen OUTPUTFILE`


### speeding up the video
`ffmpeg -itscale 0.25-i INPUTFILE -c copy OUTPUTFILE`


### replacing the audio stream
`ffmpeg -i INPUT_VIDEO -i INPUT_AUDIO -map 0:v -map 1:a -c:v copy -shortest OUTPUTFILE`

### adding an audio stream
`ffmpeg -i INPUTFILE -i INPUT_AUDIO -map 0 -map 1:a -c:v copy -shortest OUTPUTFILE`

### adding an audio stream and combining them
```
ffmpeg -i INPUT_VIDEO -i INPUT_AUDIO -filter_complex
"[0:a][1:a]amerge=inputs=2[a]" -map 0:v -map "[a]" -c:v copy -ac 2 -shortest
OUTPUTFILE
```

### rotating a video
`ffmpeg -i INPUTFILE -vf transpose=1 OUTPUTFILE`
transpose=1     positive number rotates clockwise


## SCREENRECORDER

### only screen
`ffmpeg -f x11grab -s 1280x720 -i :0.0 out.mkv`  
-f x11grab         module for video  
-i :0.0            if there is only one screen
-s 1280x720        good practice to also mention the size  
                   can be found out with *xrandr*  
**OR**
`ffmpeg -f x11grab -video_size cif -framerate 25 -i :0.0 OUT.mpg`

### screen with audio
- first find out yout input alsa device with `arecord -l`  
`ffmpeg -f x11grab -s 1280x720 -i :0.0 -f alsa -i hw:1 out.mkv`  
-f alsa            module for sound  
-i hw:1            number of alsa device  
**OR with pulseaudio**
`ffmpeg -f x11grab -s 1280x720 -i 0:0 -f alsa -i default out.mkv`

### webcam
`ffmpeg -i /dev/video0 out.mkv`

### webcam with audio
`ffmpeg -f alsa -ac 1 -i hw:1 -f video4linux2 -i /dev/video0 OUT.mpg`

### more complete example from
```
ffmpeg -f x11grab -s 1280x720 -r 30 -i :0.0 \
-f alsa -ac 2 \
-i default -vcodec libx264 -s 1280x720 \
-acodec libmp3lame -ab 128k -ar 44100 \
-threads 0 -f mkv FILENAME
```
-s resolution (input, output resolution)
-r FPS (frames per second)

