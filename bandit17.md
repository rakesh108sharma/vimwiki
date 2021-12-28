
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 17   

password: xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn 
solution: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd 

## Level Goal  

There are 2 files in the homedirectory: passwords.old and passwords.new. The
password for the next level is in passwords.new and is the only line that has
been changed between passwords.old and passwords.new

**NOTE:** if you have solved this level and see ‘Byebye!’ when trying to log into
bandit18, this is related to the next level, bandit19

### Commands you may need to solve this level
cat, grep, ls, diff

## Solution
`diff password.oold password.new`


