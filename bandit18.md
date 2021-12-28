
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 18  

password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
solution: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x 

## Level Goal  

The password for the next level is stored in a file readme in the homedirectory.
Unfortunately, someone has modified .bashrc to log you out when you log in with
SSH.

### Commands you may need to solve this level
ssh, ls, cat

## Solution

`ssh -p 2220 bandit18@bandit.labs.overthewire.org -T`  
-T   Disable pseudo-terminal allocation.

