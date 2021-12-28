[[LINUX]]
# transmission-daemon
torrent download with transmission using web browser. no gui nor cli needed

## install
* `xbps-install transmission`
* `mkdir ~/.config/transmission-daemon`
* .bashrc:
    * `export TRANSMISSION_HOME=~/.config/transmission-daemon`
* /etc/sv/transmission-daemon/run:
    * change *transmission:transmission* to your own *USER:GROUP*
* `ln -s /etc/sv/transmission-daemon /var/service/`
* browser:
    * localhost:9091

##config
* `vsv stop transmission-daemon`
* ~/.config/transmission-daemon/settings.json:
    * "download-dir": "[wherever you want]",
    * "rpc-whitelist": "127.0.0.1, 192.168.*.*",
    * change anything else
    * changes can be done over browser later
* `vsv start transmission-daemon`


