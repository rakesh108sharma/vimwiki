
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 21

password: gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
solution: Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI 

## Level Goal  

A program is running automatically at regular intervals from cron, the
time-based job scheduler. Look in /etc/cron.d/ for the configuration and see
what command is being executed.

### Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)

## Solution
1. in /etc/cron.d **cronjob_bandit22** looks promising  --> I'll **cat** it
2. it shows that **cronjob_bandit22.sh** runs every minute  --> **cat**
3. the prg reads bandit22's password and writes it in the **tmp** folder
4. just **cat** it out



