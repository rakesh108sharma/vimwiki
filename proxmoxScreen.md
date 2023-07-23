[[LINUX]]

# screen of proxmox server  
howto turn off the screen

- edit /etc/default/grub:
    - GRUB_CMDLINE_LINUX="consoleblank=60"
    - `update-grub`
    - `reboot`

