[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 28

password: 0ef186ac70e04ea33b4c1853d2526fa2
solution: bbc96594b4e001778eee9975372716b2 

## Level Goal  

There is a git repository at
ssh://bandit28-git@localhost/home/bandit28-git/repo. The password for the user
bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.

### Commands you may need to solve this level
git

## Solution

1. clone the repo 
   ```
   rm -rf /tmp/me
   mkdir /tmp/me
   cd /tmp/me
   
   git clone ssh://bandit28-git@localhost/home/bandit28-git/repo
   ```
2. the password is not in the **README** file.  
   check the history with `git log`
3. `git log -p -1` shows diff and limits output to last entry-





