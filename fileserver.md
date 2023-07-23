[[LINUX]]

# fileserver  

## inside alpine lxc  
- create alpine lxc
- `apk update && apk upgrade`
- `apk add samba`
- `mkdir /path/to/directory`
- `chmod 0777 /path/to/directory`
- edit /etc/samba/smb.conf:
    - [storage]
    -   path = /path/to/directory
- `adduser USER`
- `smbpasswd -a USER`
- `rc-update add samba`
- `rc-service samba start`
