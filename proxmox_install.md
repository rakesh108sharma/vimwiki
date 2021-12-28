[proxmox](proxmox.md)    -    [[LINUX]]

# installing proxmox

## /etc/apt/sources.list
add:
```shell
deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription
```  

## /etc/apt/sources.d/....
comment out all other repositories!

## update
`apt-get update && apt-get upgrade`  
**OR**
use the web UI for update


