[[LINUX]]  
# jellyfin for docker  
- create **config** and **cache** folders
- create somewhere a **media** folder with wanted sub-folders
 


## docker-compose  
```
---
services:
  jellyfin:
    image: lscr.io/linuxserver/jellyfin:latest
    container_name: jellyfin
    environment:
      - PUID=1000
      - PGID=1000
      - TZ="Europe/Berlin"
#      - JELLYFIN_PublishedServerUrl=192.168.0.5 #optional
    volumes:
      - /home/USER/docker/jellyfin/config:/config
      - /home/USER/docker/jellyfin/cache:/cache

#      - /DATA/Media/"TV Shows":/data/tvshows
      - /DATA/Media:/data/media
    ports:
      - 8097:8096
#      - 8920:8920 #optional
#      - 7359:7359/udp #optional
#      - 1900:1900/udp #optional
    restart: unless-stopped

```

