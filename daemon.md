[[LINUX]]
# daemon

## Liste

* system:
    * acpid
    * agetty-tty1
    * agetty-tty2
    * dbus
    * dhcpcd
    * ntpd
    * postgresql
    * sshd
    * udevd
    * uuidd
    * scron  -  suckless cron (crontab)

* virtualization:
  * virt-manager:
      * virtlockd
      * virtlogd
      * libvirtd
  * docker
  * lxd

* nfs:
    * nfs-server
    * rpcbind
    * statd

* logging:
    * nanoklogd
    * socklog-unix
* statistics Tx/Rx:
    * vnstatd

* dns cache/forward:
    * dnsmasq
    * unbound
    
* torrents:
    * transmission-daemon


## Details

### transmission-daemon
Immer wieder Probleme ... wahrscheinlich nach Updates.  
Normalerweise befindet sich die config-datei in
`~/.config/transmission-daemon/settings.json`  
Nach einem Update schaut der Daemon jedoch in
`/var/lib/transmission/.config/transmission-daemon/settings.json`  

Dort ist wichtig, daß `192.168.1.22` zu `rpc-whitelist` hinzugefügt wird.  

Die momentane *Lösung* ist, daß ich den Daemon-user in
`/etc/sv/transmission-daemon/run` von `transmission:transmission` auf
`maya:maya` ändere.  

Diese Lösung ist **ungenügend**!  
>Idee: Sollte ich eine editierte Kopie von `/etc/sv/transmission-daemon` als eigener
>Service starten, um so das Überschreiben bei einem Update zu verhindern?
