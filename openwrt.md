[[LINUX]]
# openWRT

* Failsafe Mode is useful if you have lost control of your device, and it has
become inaccessible, perhaps through a configuration error. It allows you to
reboot the router into a basic operating state, retaining all your packages and
(most) settings.  
* Factory Reset erases all your packages and settings, returning the router to its
initial state after installing OpenWrt.  
* Recovery Mode allows you to install new firmware on a router that has become corrupted.  
  
  ## Failsafe Mode
  OpenWrt allows you to boot into a failsafe mode that overrides its current configuration. If your device becomes inaccessible, e.g. after a configuration error, then failsafe mode is there to help you out. When you reboot in failsafe mode, the device starts up in a basic operating state, with a few hard coded defaults, and you can begin to fix the problem manually.

Failsafe mode cannot, however, fix more deeply rooted problems like faulty hardware or a broken kernel. It is similar to a reset, however with failsafe, you can to access your device and restore settings if desired, whereas a reset would just wipe everything.

### Entering failsafe mode
Make sure you use a wired connection, since the failsafe will disable your wireless connectivity.

On most routers, OpenWrt will blink a LED (usually “Power”, may be other) during the boot process after it gets control from the initial bootloader (like u-boot). OpenWrt will rather early in the boot cycle check if the user wants to enter the failsafe mode instead of a normal boot. It listens for a button press inside a specific two second window, which is indicated with LEDs and by transmitting an UDP package.

* **Wait for a flashing LED and press a button.** This is usually the easiest method once you figure out the correct moment.  
* Once failsafe mode is triggered, the router will boot with a network address
  of 192.168.1.1/24, usually on the eth0 network interface, with only essential
  services running. Using *telnet*, you can then mount the JFFS2 partition with
  the following command: `mount_root`  
  After that, you can start looking around and fix what’s broken. The JFFS2 partition will be mounted to /overlay, as under normal operation.  

## Factory Reset

A factory reset returns your router to the configuration it had just after flashing. This works on any install with a squashfs / overlayfs setup (the norm for most installations), since it is based on erasing and reformatting the overlayfs.

### Reset Button
On devices with a physical reset button, OpenWrt can be reset to default settings without serial or SSH access.

1. Power on the device and wait for the status led to stop flashing (or go in Failsafe Mode above).  
2. Press and keep pushed the Reset button for 10 seconds.  
3. Release the Reset button  

The device will do a Hard Factory Reset (see below) and then reboot. On some devices this operation can be slow, so wait a few minutes before connecting again.

### Soft Factory Reset
If you want a clean slate, there’s no need to flash again; just enter the following commands. Your device's settings will be reset to defaults like when OpenWrt was first installed.

Issuing “firstboot” or “jffs2reset” command will attempt to delete all files from the jffs2 overlay partition. Note that this “soft reset” is performed with file system actions, so in some cases it is not enough.

`firstboot -y && reboot now`

### Hard Factory Reset
This command will erase and reformat the whole jffs2 partition and create it again. They key for a real “hard reset” is to unmount the overlay partition first and only then issue the jffs2reset (or firstboot) command:

`umount /overlay && jffs2reset && reboot now`  
While in most cases this is producing similar end-result as the “soft reset”, this marks the whole flash area of the JFFS2 (read-write) overlay partition as a empty non-initialised jffs2 partition. Thus the partition will be re-created at the next mount, usually at the next boot. So, this hard reset bypasses the current file system of the overlay.


