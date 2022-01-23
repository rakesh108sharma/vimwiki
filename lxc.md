[[LINUX]]
# LXC / LXD

## images
list local images:
`lxc image list`

list remote images:
`lxc image images:`

search for remote images with keywords:
`lxc image images: alpine`

delete image:
`lxc image delete IMAGE-ID`

## container
launch an image (will download if image not on local host):
`lxc launch images:alpine/edge alpine`

list all containers:
`lxc list`

divers:
`lxc start|stop|restart|delete|info|show CONTAINER`

running commands within a container:
`lxc exec CONTAINER -- COMMAND`


