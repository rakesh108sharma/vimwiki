[proxmox](proxmox.md)    -    [[LINUX]]

# installing proxmox  

## SDN - software defined interfaces  
in order to activate this:
- edit: "/etc/apt/sources.list":
    - `deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription`
- `apt update`
- `apt install libpve-network-perl`
- edit "/etc/network/interfaces":
    - `source /etc/network/interfaces.d/*`
- `reboot`

SDN is now activated on the webgui at the datacenter-level.

## update
`apt-get update && apt-get upgrade`  
**OR**
use the web UI for update


