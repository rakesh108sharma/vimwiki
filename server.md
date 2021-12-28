[[LINUX]]
# server

## server liste
verschiedene server bei voidlinux, die ich mir bei zeiten anschauen möchte

### web
* lighttpd-1.4.55_1                    Secure, fast, compliant and very flexible web-server
* darkhttpd-1.12_3                     Small and secure static webserver
* gatling-0.15_8                       High performance web server
* hiawatha-10.10_1                     Advanced and secure webserver for Unix
* mongoose-6.17_1                      Easy to use Web server
* h2o-2.2.6_1                          Optimized HTTP server with support for HTTP/1.x and HTTP/2
* servy-1.0.0_2                        A tiny little web server
* thttpd-2.29_2                        Tiny/turbo/throttling HTTP server
* python-Cheroot-8.3.0_1               High-performance, pure-Python HTTP server (Python2)
* fcgi-2.4.0_5                         Fast, open, and secure Web server interface

### ftp
#### server
* bftpd-5.5_1                  Simple FTP server
* hooktftp-1.1.0_1             Hook based tftp server
* proftpd-1.3.6_2              Highly configurable GPL-licensed FTP server software
* twoftpd-1.43_4               Simple secure efficient FTP server

#### client
* filezilla-3.48.0_1           Fast and reliable FTP, FTPS and SFTP client
* tnftp-20151004_8             NetBSD enhanced ftp client
* lftp-4.9.1_1                 Sophisticated FTP/HTTP client
* gftp-2.0.19_6                Graphical file transfer client

* inetutils-ftp-1.9.4_11       GNU network utilities - ftp client and server (file transfer protocol)
* inetutils-tftp-1.9.4_11      GNU network utilities - tftp client and server (trivial file transfer protocol)
* tftp-hpa-5.2_5               Official tftp client and server

#### filesystem
* lftpfs-0.4.3_2               Filesystem with caching based on FUSE and LFTP
* curlftpfs-0.9.2_6            A FTP filesystem based on cURL and FUSE
* obexfs-0.12_4                FUSE based filesystem using ObexFTP

#### other??
* ncftp-3.2.6_2                Set of application programs implementing the File Transfer Protocol
* obexftp-0.24.2_2             OBEX transfer utilities
* uftp-4.10.1_1                Encrypted multicast file transfer program
* vsftpd-3.0.3_12              FTP deamon with focus on security

### other
* 3proxy-0.8.13_1                      3proxy tiny proxy server
* arcan-0.5.5.2_3                      Combined display server, multimedia framework and game engine
* dropbear-2019.78_1                   Small SSH server and client
* gerbera-1.3.1_2                      UPnP Media Server based on MediaTomb
* tvheadend-4.2.8_3                    TV streaming server

## torrent
```
apk add transmission-cli transmission-daemon  
rc-update add transmission-daemon  

rc-service transmission-daemon start  
rc-service transmission-daemon stop  

```  

`nano /var/lib/transmission/config/settings.json`  
>"rpc-whitelist": "127.0.0.1,192.168.*.*",  

`rc-service transmission-daemon start`  

->browser-> port 9091


## file server (klein) mit samba  
Der CT muß 'privileged' sein!

* im virt-manager eine Festplatte 'raw' erstellen  
* node->ZFS->create ZFS  
    * untick 'add storage'  
* node->shell  
    * zfs create [FESTPLATTE-NAME]/share  
    * `nano /etc/pve/lxc/[CT-ID].conf`  
        mp0 FESTPLATTE-NAME/share,mp=[MOUNTPOINT]  
        eg: mp0 tor-festplatte/share,mp=/var/lib/transmission/config/torrents  
* CT starten   
* CT->shell  
    * `apt install samba`
    * `mv /etc/samba/smb.conf /etc/samba/smb.bak`
    * `nano /stc/samba/smb.conf`  
        ```
        [global]  
        map to guest = Bad User  
        workgroup = (bei linux keine Ahnung)  
        
        [data]  
        path = /var/lib/transmission/config/torrents  
        read only = no  
        guest ok = yes  
        ```  
    * `rc-update add samba`  
    * `rc-service samba start`
* ->browser   smb://IP
* ->host PC: `smbclient \\\\[PC-lxc-NAME]\\data`
    eg: `smbclient \\\\torrent\\data`
      
## file server (klein) mit nfs
same as above with samba (except for the samba part)  
* `apk add nfs-utils libnfs`
* create and modify the dir to share:
    * `sudo mkdir /public`
    * `sudo chown nobody:nogroup /public`
    * `sudo chmod 777 /public`
* `nano /etc/exports`  
    /DIR_TO_SHARE *(ro,sync)  
    eg: /public 192.168.1.0/24(rw,sync)
* fstab (client):
    * 192.168.1.X:/public /home/maya/nfs-void nfs default 0 0 
    * can be mounted (if not present at boot): `sudo mount /home/maya/nfs-void`


