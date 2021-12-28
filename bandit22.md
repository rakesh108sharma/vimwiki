
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 22

password: Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI 
solution: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n 

## Level Goal  

A program is running automatically at regular intervals from cron, the
time-based job scheduler. Look in /etc/cron.d/ for the configuration and see
what command is being executed.

**NOTE:** Looking at shell scripts written by other people is a very useful skill.
The script for this level is intentionally made easy to read. If you are having
problems understanding what it does, try executing it to see the debug
information it prints.

### Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)

## Solution

1. I see in `/etc/cron.d/` a cronjob for **bandit23**
2. ..it shows, there is a shellscript `cronjob_bandit23.sh`
3. reading it, I can ssee that the script regularely writes bandit's password to
   a **md5sum** file in `tmp/`
4. ..I use part of the script in the terminal:
    1. `echo I am user bandit23 | md5sum | cut -d ' ' -f 1`
    2. it returns the md5sum **8ca319486bfbbc3663ea0fbe81326349**
    3. `cat /tmp/8ca319486bfbbc3663ea0fbe81326349`



