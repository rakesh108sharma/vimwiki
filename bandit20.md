
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 20

password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
solution: gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr 

## Level Goal  

There is a setuid binary in the homedirectory that does the following: it makes
a connection to localhost on the port you specify as a commandline argument. It
then reads a line of text from the connection and compares it to the password in
the previous level (bandit20). If the password is correct, it will transmit the
password for the next level (bandit21).

**NOTE:** Try connecting to your own network daemon to see if it works as you think

### Commands you may need to solve this level
ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z)

## Solution
**complex**
- find a **free** port
- we need 2 terminals
- first one listens to a port
- second runs the binary (as user bandit21)
- back two the first terminal we enter bandit20's password
- we get bandit21's password

1. `nmap localhost`  (port 20000 is free - I use this one)
2. `nc -lp 20000 &`
3. `./suconnect 20000 &`
4. `fg`  (bring the job with **nc** back to the foreground)
5. enter **bandit20**'s password

### alternative solution
1. `nmap localhost`
2. `echo "gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr" | nc -l localhost -p 20000 &`
3. `./suconnect 20000`

