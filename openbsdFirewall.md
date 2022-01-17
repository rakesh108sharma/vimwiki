[[INDEX]] [[OPENBSD]]

# Openbsd as a betwork firewall
- install openbsd by deselecting:
    - `game64.tgz`
    - `comp64.tgz`   - compilers
    - all 'x' (xbase, xshare, xfont,xserv)
- update:
    - `fw_update`
    - `syspatch`
    - `reboot`
- user managment:
    - `adduser` (add to *wheel*)
    - `rmuser`
    - lock and unlock user account:
        - `usermod -Z USERNAME`
        - `usermod -U USERNAME`
- service managment:
    - `rcctl enable|diasable|start|stop|restart|reload|status`
- network managment:
    - interfaces are configured in `/etc/hostname.INTERFACE`
    - LAN `/etc/hostname.em0`:
        - `inet 192.168.11.1 255.255.255.0`
    - WAN `/etc/hostname.em1`:
        - `inet 192.168.1.12 255.255.255.0`
        - `!route add default 192.168.1.1`
- enable IP routing in `/etc/sysctl.conf`:
    - `net.inet.ip.forwarding=1`
- PF:
    - check file          `pfctl -nf /etc/pf.conf`
    - load  file          `pfctl -f /etc/pf.conf`
    - enable  pf          `pfctl -e`
    - disable pf          `pfctl -d`
    - show statistics     `pfctl -si`
    - show states         `pfctl -ss`
    - `/etc/pf.conf`:
        - 
          `LAN="em0"`
          `WAN="em1"`
          `set skip on lo0`
          `set block-policy drop`
          `block drop all`
          `pass in on $LAN from $LAN:network to any keep state`
          `pass out on $WAN from $LAN:network to any nat-to ($WAN) keep state` 
          `pass out on $WAN from $WAN:network to any keep state`
          
          
