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
- transmission                 - torrent
- droppy                       - drop box for files
- filebrowser                  - drop box (wie droppy)
- pihole                       - ad blocker
- whoogle                      - search engine
- freshrss                     - rss reader
- shiori                       - drop box for URL's
- bitwarden                    - password manager
- homer                        - dashboard for browser
- [heimdall](heimdall.md)                     - dashboard for browser
- [gollum](gollum.md)                       - personal wiki
