[[LINUX]]

# docker
- in order to install docker directly from **docker.com**:
`curl -sSL https://get.docker.com | sh`

- add user to **docker group**:
    - `sudo usermod -aG docker USER`

## portainer
web gui managment system for docker.  
Another one is **yacht**.  

### install
`docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock  portainer/portainer-ce`

**install for raspberry**
the raspbery is an **arm** computer
`sudo docker pul portainer/portainer-ce:linux-arm`  
`sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:linux-arm`  


### Templates
[original App](https://raw.githubusercontent.com/portainer/templates/master/templates-2.0.json)
[SelfhostedPro](https://raw.githubusercontent.com/SelfhostedPro/selfhosted_templates/master/Template/portainer-v2.json)


## interesting containers
- [transmission](transmission.md)                 - torrent
- droppy                       - drop box for files
- [filebrowser](filebrowser.md)                  - drop box (wie droppy)
- pihole                       - ad blocker
- whoogle                      - search engine
- freshrss                     - rss reader
- shiori                       - drop box for URL's
- bitwarden                    - password manager
- homer                        - dashboard for browser
- [heimdall](heimdall.md)                     - dashboard for browser
- [gollum](gollum.md)                       - personal wiki
- [jellyfin](jellyfin.md)                     - movie streamer 
- flatnotes                    - note taking 


## short commands  
### ctop  
ctop checks all container for health etc.  
create this alias to start **ctop** as a container which will be destroyes on exit. 
`alias dockercheck='docker run --rm -ti \
--name=ctop \
--volume /var/run/docker.sock:/var/run/docker.sock:ro quay.io/vektorlab/ctop:latest'`

