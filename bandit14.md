[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 14

password: 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
solution: BfMYroe26WYalil77FoDi9qh59eK5xNr 

## Level Goal  

The password for the next level can be retrieved by submitting the password of
the current level to port 30000 on localhost.

### Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap

### Helpful Reading Material
How the [Internet](https://www.youtube.com/watch?v=7_LPdttKXPc) works in 5 minutes (YouTube) (Not completely accurate, but good enough for beginners)
IP [Addresses](http://computer.howstuffworks.com/web-server5.htm)
IP [Address](https://en.wikipedia.org/wiki/IP_address) on Wikipedia
[Localhost](https://en.wikipedia.org/wiki/Localhost) on Wikipedia
[Ports](http://computer.howstuffworks.com/web-server8.htm)
Port (computerter
[networking](https://en.wikipedia.org/wiki/Port_(computer_networking))) on Wikipedia

## Solution

1. `nmap -p 30000 localhost`  
   ANSWER: 30000/tcp open  ndmps
 
2. `telnet localhost 30000`  
   once connected, enter the password of this level

## Alternative Solution

`echo "4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e" | nc localhost 30000`  



