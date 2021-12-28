[[LINUX]]
# youtube-dl
- can be installed with *pip*

## troubleshooting
error: 
    `YouTube said: Unable to extract video data` 
solution:
    update youtube-dl
    `pip install --upgrade youtube-dl`  

## using
check for available formats:
`youtube-dl -F URL`  

download video 'mp4':
`youtube-dl -f 22 URL`  

download audio in 'm4a' format:
`youtube-dl -f 140 URL`  

download and transform into 'mp3' format:
`youtube-dl -x --audio-format mp3 --prefer -ffmpeg URL`  



     
