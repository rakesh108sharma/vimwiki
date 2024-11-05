[[LINUX]]  

# filebrowser  
a docker image

## docker-compose  
- find out user UID and GUID
- choose a port
- volumes:
    - **/srv** is the folder which will be presented on the web UI
    - **/database.db** is the volume pointing at the database:
        - for this the folders AND the database.db have to be created

```
---
services:
  file-browser:
    image: filebrowser/filebrowser
    user: 1000:1000
    ports:
      - 8081:80
    volumes:
      - /home/USER/FOLDER-TO-PRESENT/:/srv
      - /home/USER/docker/filebrowser/filebrowser.db:/database.db
#     - /home/USER/docker/filebrowser/settings.json:/config/settings.json
    restart: unless-stopped
    security_opt:
      - no-new-privileges:true
```

