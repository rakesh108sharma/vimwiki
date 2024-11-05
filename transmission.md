[[LINUX]]  

# transmission (docker)  
- check **UID** and **GID**
- create a **download** and **watch** folder


## docker-compose  
example:  
```
---
services:
  transmission:
    image: lscr.io/linuxserver/transmission:latest
    container_name: transmission
    environment:
      - PUID=1000
      - PGID=1000
      - TZ="Europe/Berlin"
#      - TRANSMISSION_WEB_HOME= #optional
#      - USER= #optional
#      - PASS= #optional
#      - WHITELIST= #optional
#      - PEERPORT= #optional
#      - HOST_WHITELIST= #optional
    volumes:
      - /home/USER/docker/transmission:/config
      - /DATA/Downloads:/downloads
      - /home/USER/downloads:/watch
    ports:
      - 9091:9091
      - 51413:51413
      - 51413:51413/udp
    restart: unless-stopped

```
