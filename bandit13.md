[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 13

password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL 
solution: 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e

## Level Goal  

The password for the next level is stored in /etc/bandit_pass/bandit14 and can
only be read by user bandit14. For this level, you don’t get the next password,
but you get a private SSH key that can be used to log into the next level. Note:
localhost is a hostname that refers to the machine you are working on

### Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap

### Helpful Reading Material
[SSH OpenSSH Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)  

## Solution  
`ssh bandit14@localhost -i sshkey.private`  
-i identity_file
   Selects a file from which the identity (private key) for public key authentication is read.

