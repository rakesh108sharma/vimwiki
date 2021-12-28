[[LINUX]]
# GNS3

## routed network
setting up a simple routed network:
* 2 routers (c3745)
* 2 VPCS

### VPCS config
* PC1
  `ip 4.4.4.1/24 4.4.4.2`
  `save`
* PC2
  `ip 1.1.1.1/24 1.1.1.2`
  `save` 
  
### c3745 config
* R1
  ```
  configure t
  interface fastethernet 0/0
  ip address 10.0.0.1 255.255.255.0
  no shutdown
  end
  
  configure t
  interface fastethernet 0/1
  ip address 4.4.4.2 255.255.255.0
  no shutdown
  end
  
  configure t
  ip route 0.0.0.0 0.0.0.0 10.0.0.2
  exit
  
  write memory
  ```
  
* R2
  ```
  configure t
  interface fastethernet 0/0
  ip address 10.0.0.2 255.255.255.0
  no shutdown
  end
  
  configure t
  interface fastethernet 0/1
  ip address 1.1.1.2 255.255.255.0
  no shutdown
  end
  
  configure t
  ip route 0.0.0.0 0.0.0.0 10.0.0.1
  exit
  
  write memory
  ```
