
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 27

password: 3ba3118a22e93127a4ed485be72ef5ea
solution: 0ef186ac70e04ea33b4c1853d2526fa2 

## Level Goal  

There is a git repository at
ssh://bandit27-git@localhost/home/bandit27-git/repo. The password for the user
bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.

### Commands you may need to solve this level
git

## Solution

1. make a directory in /tmp/
2. `ssh://bandit27-git@localhost/home/bandit27-git/repo`
3. `cat repo/README`

