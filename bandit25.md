
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 25

password: uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG
solution: 5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z 

## Level Goal  

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user
bandit26 is not /bin/bash, but something else. Find out what it is, how it works
and how to break out of it.

### Commands you may need to solve this level
ssh, cat, more, vi, ls, id, pwd

## Solution
1. ` ssh bandit26@localhost -i bandit26.sshkey` prints a text and closes the
   connection.
2. that is because bandit26 does not have a shell: 
   `cat /etc/passwd | grep bandit26`
3. `cat /usr/bin/showtext`  
   **more** is being called
4. we need to resize the terminal in order to *catch* **more**
5. pressing **v** starts the editor (vi)
6. in **vi** we can open bandit26's password file  
   `:e /etc/bandit_pass/bandit26`
   




