
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 16

password: cluFn7wTiGryunymYOu4RcffSxQluehd
solution: xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn 

## Level Goal  

The credentials for the next level can be retrieved by submitting the password
of the current level to a port on localhost in the range 31000 to 32000. First
find out which of these ports have a server listening on them. Then find out
which of those speak SSL and which don’t. There is only 1 server that will give
the next credentials, the others will simply send back to you whatever you send
to it.

### Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap

### Helpful Reading Material
Port scanner on Wikipedia

## Solution
1. `nmap localhost -p 31000-32000 -A`
2. we have to save the key **BUT** do not have write privelege:
    ```
    rm -rf /tmp/name123
    mkdir /tmp/name123
    cd /tmp/name123
    ´´´
3. `echo "cluFn7wTiGryunymYOu4RcffSxQluehd" | openssl s_client -connect
   localhost:31790 -ign_eof > sshkey.private`
4. `chmod 400 sshkey.private`
5. `ssh -i sshkey.private bandit17@localhost`
6. **PASSWORD** `cat /etc/bandit_pass/bbandit17`
7. **CLEAN**
   ```
   exit
   rm -rf sshkey.private
   exit
   ```

   

