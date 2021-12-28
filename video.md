[[LINUX]]
# video

## Troubleshooting Screen Tearing
- first find which kernel driver is in use:
  `lspci -nnk | grep -i -EA3 "3d|display|vga"`  
- apply the fix for your driver
- reboot

### driver: radeon
edit OR create `/etc/X11/xorg.conf`  

```
Section "Device"
        Identifier  "Radeon"
        Driver      "radeon"
        Option      "TearFree" "on"
EndSection
```

### driver: amdgpu
edit OR create `/etc/X11/xorg.conf.d/20-amdgpu.conf`  

```
Section "Device"
        Identifier  "AMD"
        Driver      "amdgpu"
        Option      "TearFree" "true"
EndSection
```

### driver: intel
edit OR creat `/etc/X11/xorg.conf.d/20-intel-gpu.conf`

```
Section "Device"
        Identifier  "Intel Graphics"
        Driver      "intel"
        Option      "TearFree"  "true"
EndSection
```

if tearing still persist, the add additionaly:
    `Option      "AccelMethod"  "uxa"`  


