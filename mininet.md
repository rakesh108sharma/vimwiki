[[LINUX]]
# mininet
learn development tools.

## network
### start  
`sudo mn --topo single,3 --mac --switch ovsk --controller remote`

### end network && clean  
`mininet> exit`
`sudo mn -c`

### start wireshark  
```
ssh -X mininet@[guest ip address]
sudo wireshark &         /* ignore warning: running as root */
sudo controller ptcp:6633
```
_needs to be run from another ssh-session_  
`sudo mn --topo single,3 --mac --switch ovsk --controller remote`

## ovs-ofctl Example Usage.
The show command connects to the switch and dumps out its port state and capabilities.  
`sudo ovs-ofctl show s1`  
`sudo ovs-ofctl dump-flows s1`

### ping gets no reply?
As you saw before, switch flow table is empty. Besides that, there is no controller connected to the switch and therefore the switch doesn't know what to do with incoming traffic, leading to ping failure.  

You'll use ovs-ofctl to manually install the necessary flows. In your SSH terminal:

 `sudo ovs-ofctl add-flow s1 in_port=1,actions=output:2`
 `sudo ovs-ofctl add-flow s1 in_port=2,actions=output:1`

### clearing existing flows
`sudo ovs-ofctl del-flows s1`  



