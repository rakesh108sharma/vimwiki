[[LINUX]]
# OSI layer model

|-
| Nr. | layer        | data     | function                         | prg/tools         |
| 7   | application  | data     | HTTP/FTP/IRC/SSH/DNS             |                   |
| 6   | presentation | data     | SSL/SSH/FTP/IMAP/MPEG/JPEG       |                   |
| 5   | session      | data     | api/socket                       |                   |
| 4   | transport    | segments | TCP/UDP                          | ip / route / ping |
| 3   | network      | packets  | IP/ICMP/IPSes/IGMP               | netstat / ss      |
| 2   | data link    | frames   | ethernet/PPP/switchbridg         | arp               |
| 1   | physical     | bits     | coax/fiber/wireless/hub/repeater | net-tools         |
