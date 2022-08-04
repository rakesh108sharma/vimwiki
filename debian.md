[[LINUX]]
# debian  

## install  
do **NOT** install from the suggested install link!  
**instead** install *firmware-testing-amd64-netinst.iso*:  
- download button
- follow *Unofficial non-free images including firmware*  
- weekly builds
- amd64
- iso-cd
- firmware-testing-amd64-netinst.iso

burn the image and install.  
install without the graphic installer  


## post install  
- add **contrib** and **non-free** repos
- install drivers:
    - AMD open source drivers are good
    - proprietary drivers:
        - ```sudo apt install firmware-linux firmware-linux-nonfree libdrm-amdgpu1 xserver-xorg-video-amdgpu```  
- install microcode:
    - **either** intel-microcode **or** amd64-microcode
- install build-essential:
    - `sudo apt install build-essential dkms linux-headers-$(uname -r)`
- install ubuntu-restricted-extras:
    - `sudo apt install ttf-ms-corefonts-installer rar unrar libavcodec-extra gstreamer1.0-libav gstreamer1.0-plugins-ugly gstreamer1.0-vaapi`
- configure swappiness (/etc/sysctl.conf):
    - `vm.swappiness=10`
- install a firewall:
    - `sudo apt install ufm`
    - `sudo ufw enable`
- install a backup programm:
    - timeshift
- enable gnome-extensions:
    - goto https://extensions.gnome.org and install
- enable tray icons:
    - goto https://extensions.gnpme.org
    - search for *topicons*
    - install *TopiconsPlus*
    - goto *settings* and move icons to the right
    - 

## package managment  
use **nala** as a frontend to **apt**  
enable **flatpak**  

## swap  
adding a swap file instead of a swap partition.  

- create a file:
    - `sudo fallocate -l 2G /swapfile`
- change permissions:
    - `sudo chmod 600 /swapfile`
- create file system:
    - `sudo mkswap /swapfile`
- edit /etc/fstab:
    - `/swapfile swap swap defaults 0 0`
- reboot


