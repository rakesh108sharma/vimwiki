[proxmox](proxmox.md)    -    [[LINUX]]

# SPICE

## client
on the client machine 2 packages must be installed:
    - qemu-kvm
    - virt-viewer


## server
while creating a new VM, in the menu choose:
    - System  -->  **SPICE**
    - (SPICE Memory  -> 16-32 M is enough)
    - Memory  -->  **4096**  (min 4G)

once the VM has been created, go to the menu:
    - Options -->  Spice Enhancements  -->  **all**

start the VM:
    - console  -->  SPICE  -->  **open with remote-viewer**
    
    
