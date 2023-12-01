[[LINUX]]  

# NFS server  
## server side  
- install:
    - nfs-utils (voidlinux)
    - nfs-kernel-server (debian)
- create FOLDER and SUBDIRS to share:
    - ex `mkdir /nfs /nfs/music`
- edit `/etc/exports` to configure FOLDER and who is allowed to connect:
    - `/path/to/FOLDER HOST-IP/NETMASK(OPTIONS)`
    - ex: `/nfs 192.168.1.0/24(rw,sync)`




## client side 
- install:
    - nfs-commom
- create DEST-FOLDER to which FOLDER will be attached
- mount FOLDER:
    - `sudo mount 192.168.1.13:/nfs path/to/DEST-FOLDER`
    - ex `sudo mount 192.168.1.13/nfs /home/maya/nfs

### with autofs  
- install:
    - autofs
- edit `/etc/auto.master` by adding the DEST-FOLDER:
    - `path/to/DEST-FOLDER /etc/auto.nfs --ghost --timeout=60`
    - ex `/home/maya/nfs /etc/auto.nfs --ghost --timeout=60`
- edit `/etc/auto.nfs` and add the SUBDIRS from the server side:
    - `DEST-SUBFOLDER -fstype=nfs4,rw SERVER-IP:SRC-PATH-TO-SUBFOLDER`
    - `music -fstype=nfs4,rw 192.158.1.13:/nfs/music`
- restart autofs daemon
    
