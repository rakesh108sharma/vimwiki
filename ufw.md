[[LINUX]]

# ufw
`ufw enable`
`ufw disable`
`ufw status numbered`

## Shut everything down
```
ufw default deny incoming
ufw default deny forward
ufw default deny outgoing
```

## now punch holes through the wall
- find the name of your interface:
`ip a`  
- Allow DNS, HTTP, and HTTPS traffic out:
```
ufw allow out on <interface> to 1.1.1.1 proto udp port 53 comment 'allow DNS on <interface>'
ufw allow out on <interface> to any proto tcp port 80 comment 'allow HTTP on <interface>'
ufw allow out on <interface> to any proto tcp port 443 comment 'allow HTTPS on <interface>'
```

## monitor the firewall
`tail -f /var/log/ufw.log`  


