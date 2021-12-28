
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 19

password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
solution: GbKksEFF4yrVs6il55v6gwY5aVje5f0j 

## Level Goal  

To gain access to the next level, you should use the setuid binary in the
homedirectory. Execute it without arguments to find out how to use it. The
password for this level can be found in the usual place (/etc/bandit_pass),
after you have used the setuid binary.

### Helpful Reading Material
setuid on Wikipedia

## Solution
1. use the binary to create a tmp directory:
    1. `./bandit20-do mkdir /tmp/ich`
2. use binary to copy bandit20 th password file:
    1. `./bandit20-do cp /etc/bandit_pass/bandit20 /tmp/ich/`
3. *cat* it out:
    1. `./bandit30-do cat /tmp/ich/bandit20`
!! actually it looks like you can cat it out whithin the *etc* folder.



