[[LINUX]]

**NOT WORKING**
# stream videos over a web server  
instead of installing a over complex/complicated, cluttered and TMI (too much information) media
server like plex/jellyfin/kodi etc ... just stream media via a web server.  

- install nginx
- edit:
    - `root DIRECTORY`
    - add to `location / { autoindex on; }`
- start nginx daemon

